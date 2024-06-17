# Introduction 
- Simple Proof-of-Concept using NFC Reader component in Power Apps
- Read NFC chip in employee badge to extract unique employee id (Text field)
- Can be used for quick attendance taking during in-house classroom trainings, daily production toolbox meetings etc
- Extracted emp id can be used to lookup other employee data such as email address, O365 profile info etc.
[See image capture]


# ReadNFC function
OnSelect:
With(ReadNFC(),
    If(!IsBlank(Identifier),Notify("NFC detected"));
    Set(id, Coalesce(Identifier, "No ID"));
    ForAll(NDEFRecords, Collect(tagRecords, {ID: id, Value: Coalesce(Text, URI)})));
