## SoapFormatter cannot deserialize Hashtable and similar ordered collection objects

### Scope
Minor

### Version Introduced
4.5

### Source Analyzer Status
Available

### Change Description
The SoapFormatter does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version. Specifically, some ordered collections (like Hashtable) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET 4.0 if they were serialzied with .NET 4.5.  
Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.

- [ ] Quirked
- [ ] Build-time break

### Recommended Action
SoapFormatter serialization should be replaced with BinaryFormatter serialization or NetDataContractSerialization to be resilient to .NET Framework changes.

### Affected APIs
* `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)`
* `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])`
* `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)`
* `M:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

### Category
Serialization

[More information](https://msdn.microsoft.com/en-us/library/hh367887\(v=vs.110\).aspx#core)

<!-- breaking change id: 1 -->
