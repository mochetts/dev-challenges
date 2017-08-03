# Ruby Calendar

The half-baked mission, should you choose to accept it, is as follows:

Implement a simple Ruby-console-based calendar app from scratch. (No calendar gems, please.) The program should allow users to create new calendars, then add, update, remove, and display events from those calendars.

Each calendar must have a name.

Events must have a name and a start time. Additionally, each event should have either an end time _or_ be flagged as an all-day event. Each event may also have an optional location. If an event has a location, the location must have a name and can also have an address, city, state, and zip.

Calendars should support the following methods:

- `#add_event(name, params)` – Adds an event to the calendar. 
- `#events` – Returns all events for the calendar.
- `#events_with_name(name)` – Returns events matching the given name.
- `#events_for_date(date)` – Returns events that occur during the given date.
- `#events_for_today` – Returns events that occur today.
- `#events_for_this_week` – Returns events that occur within the next 7 days.
- `#update_events(name, params)` – For all calendar events matching the given name, then update the event's attributes based on the given params.
- `#remove_events(name)` – Removes calendar events with the given name.

Below are some examples of how one might interact with the app.


### Initialize the Calendar
```ruby
cal = Calendar.new("Cathy's Calendar")
```

### Add Events to the Calendar
```ruby
cal.add_event("Cathy's Party",             # name is required
  all_day: false,                          # all_day is optional (defaults to false)
  start_time: Time.new(2017, 8, 4, 20, 0), # start_time is required
  end_time: Time.new(2017, 8, 4, 23, 59),  # end_time is required UNLESS all_day is true
  location: {                              # location is optional
    name: 'Barcade',                         # name is required
    address: '148 W 24th St',                # address is optional
    city: 'New York',                        # city is optional
    state: 'NY',                             # state is optional
    zip: '10011'                             # zip is optional
  }
)

cal.add_event('Brunch with Friends',
  start_time: Time.new(2017, 8, 5, 11, 30),
  end_time: Time.new(2017, 8, 5, 13, 0),
  location: {
    name: "Jack's Wife Freda",
    address: '224 Lafayette St',
    city: 'New York',
    state: 'NY',
    zip: '10012'
  }
)

cal.add_event('Dog Walking',
  start_time: Time.new(2017, 8, 5, 15, 30),
  end_time: Time.new(2017, 8, 5, 16, 30),
  location: {
    name: 'Brooklyn Paws, Inc.',
    address: '110 York St',
    city: 'Brooklyn',
    state: 'NY',
    zip: '11201'
  }
)

cal.add_event("Andy Warhol's Birthday",
  all_day: true,
  start_time: Time.new(2017, 8, 6)
)

cal.add_event('Cipherhealth Interview',
  start_time: Time.new(2017, 8, 8, 14, 00),
  end_time: Time.new(2017, 8, 8, 15, 30),
  location: {
    name: 'Cipherhealth',
    address: '555 8th Ave',
    city: 'New York',
    state: 'NY',
    zip: '10018'
  }
)

cal.add_event('VACATION!',
  start_time: Time.new(2017, 8, 19, 10),
  end_time: Time.new(2017, 8, 27, 14, 0),
  location: {
    name: 'Tulum, Mexico'
  }
)
```

### Display All Events for a Calendar
```ruby
cal.events
# Cathy's Party
# ...Starts: August 4, 2017 at 08:00 pm
# ...Ends: August 4, 2017 at 11:59 pm
# ...Location: Barcade, 148 W 24th St, New York, NY, 10011
# ---------------------------------------------------------------------
# Brunch with Friends
# ...Starts: August 5, 2017 at 11:30 am
# ...Ends: August 5, 2017 at 01:00 pm
# ...Location: Jack's Wife Freda, 224 Lafayette St, New York, NY, 10012
# ---------------------------------------------------------------------
# Dog Walking
# ...Starts: August 5, 2017 at 03:30 pm
# ...Ends: August 5, 2017 at 04:30 pm
# ...Location: Brooklyn Paws, Inc., 110 York St, Brooklyn, NY, 11201
# ---------------------------------------------------------------------
# Andy Warhol's Birthday
# ...Date: August 6, 2017 (All Day)
# ---------------------------------------------------------------------
# Cipherhealth Interview
# ...Starts: August 8, 2017 at 02:00 pm
# ...Ends: August 8, 2017 at 03:30 pm
# ...Location: Cipherhealth, 555 8th Ave, New York, NY, 10018
# ---------------------------------------------------------------------
# VACATION!
# ...Starts: August 19, 2017 at 10:00 am
# ...Ends: August 27, 2017 at 02:00 pm
# ...Location: Tulum, Mexico
# ---------------------------------------------------------------------
```

### Find and Filter Calendar Events
```ruby
cal.events_with_name("Cathy's Party")
# Cathy's Party
# ...Starts: August 4, 2017 at 08:00 pm
# ...Ends: August 4, 2017 at 11:59 pm
# ...Location: Barcade, 148 W 24th St, New York, NY, 10011

cal.events_for_date(Date.new(2017, 8, 4))
# Cathy's Party
# ...Starts: August 4, 2017 at 08:00 pm
# ...Ends: August 4, 2017 at 11:59 pm
# ...Location: Barcade, 148 W 24th St, New York, NY, 10011

# Assuming today is August 5th, 2017
cal.events_for_today
# Brunch with Friends
# ...Starts: August 5, 2017 at 11:30 am
# ...Ends: August 5, 2017 at 01:00 pm
# ...Location: Jack's Wife Freda, 224 Lafayette St, New York, NY, 10012
# ---------------------------------------------------------------------
# Dog Walking
# ...Starts: August 5, 2017 at 03:30 pm
# ...Ends: August 5, 2017 at 04:30 pm
# ...Location: Brooklyn Paws, Inc., 110 York St, Brooklyn, NY, 11201
```

### Update Calendar Events
```ruby
cal.update_events('Cipherhealth Interview',
  start_time: Time.new(2017, 8, 8, 15, 00),
  end_time: Time.new(2017, 8, 8, 16, 30)
)
# Cipherhealth Interview
# ...Starts: August 8, 2017 at 03:00 pm
# ...Ends: August 8, 2017 at 04:30 pm
# ...Location: Cipherhealth, 555 8th Ave, New York, NY, 10018
```

### Remove Calendar Events
```ruby
cal.remove_events("Andy Warhol's Birthday")
# Andy Warhol's Birthday
# ...Date: August 6, 2017 (All Day)
```

You don't need to worry about persisting events in a database; in-memory storage is fine for this exercise. Also, we've suggested an application interface and possible output in the examples above, but feel free to be creative!

### Bonus Points

- Use something like [Chronic](https://github.com/mojombo/chronic) to support start and end times entered as more human-friendly strings, e.g. `start_time: '8/2/17 3:30pm'`
- Validate calendar, event, and location parameters and provide helpful error messaging.
