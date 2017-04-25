## MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer

### Scope
Major

### Version Introduced
4.5

### Source Analyzer Status
Available

### Change Description
Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (XmlSerializer object). Trying to serialize a MEF catalog throws an exception.

- [ ] Quirked
- [ ] Build-time break

### Recommended Action
Can no longer use MEF to create a serializer

### Affected APIs
* Not detectable via API analysis

### Category
Managed Extensibility Framework (MEF)

[More information](https://msdn.microsoft.com/en-us/library/hh367887#MEF)

<!-- breaking change id: 12 -->
