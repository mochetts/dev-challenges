The application is a simple bot which based on your key metrics verify your health.
When we run the application Doctor should ask you for your key metrics.

You can send as many key metrics as you want.

If you send key metric which is not supported you should receive message with allowed key metrics.

Key Metrics should be saved in valid format. If not valid send a proper message.
You should be able to ask for a status of particular key metric but also for a diagnosis.

### Example conversation

```
Doctor:   Welcome. I am Doctor AI. What are your key metrics?
Patient:  Age 24
Patient:  Weight 70 kg, Height 180 cm, Blood Pressure 139/89
Patient:  Verify Blood Presure
Doctor:   Your Blood presure is to high. It should be in 120-129/80-84
Patient:  *Request Diagnosis*
Doctor:   You should eat more vegetables.
Patient:  Thank you.
Doctor:   You're welcome. Have a nice day.
Doctor:   Welcome. I am Doctor AI. What are your key metrics?
```

### Allowed Key Metrics

- Age
- Weight
- Height
- Blood Pressure

### Commands

-  __Add a new Key Metric:__ `{{ Key Metric Name }} {{ Value }} {{ unit (optional) }}`
- __Check the status of a Key Metric:__ `Verify {{ Key Metric Name }}`
- __Make a diagnosis based all all the available Key Metrics:__ `Request Diagnosis`

### Requirements

- Age, Weight, Height and one additional key metric are required
- In the future we would like to add more key metrics
- There can be a case where Doctor will not be able to make a diagnosis
