## AesCrytpServiceProvider decryptor provides a reusable transform

### Scope
Minor

### Version Introduced
4.6.2

### Source Analyzer Status
Investigating

### Change Description
Starting with apps that target the .NET Framework 4.6.2, the `T:System.Security.Cryptography.AesCryptoServiceProvider` decryptor provides a reusable transform. After a call to `TransformFinalBlock`, the transform is reinitialized and can be reused.
For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling `TransformBlock` after a call to `TransformFinalBlock` throws a `T:System.Security.Cryptography.CryptographicException` or produces corrupted data.

- [X] Quirked AppContext or config files. Needs to be turned on automatically for some situations.
- [ ] Build-time break

### Recommended Action
The impact of this change should be minimal, since this is the expected behavior.

Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:

   ```xml
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
  </runtime>
   ```

In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:

   ```xml
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
   </runtime>
   ```

### Affected APIs
- `M:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor`

### Category
Core

<!--
    ### Original Bug
    205301
-->

<!-- breaking change id: 165 -->
