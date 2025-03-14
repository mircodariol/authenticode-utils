# PowerShell Scripts

## `get-authenticode-signatures.ps1`

This script checks the Authenticode signatures of files in a specified directory.

### Synopsis

This script recursively scans a directory for files with `.exe`, `.dll`, and `.ps1` extensions. It retrieves the Authenticode signature of each file and collects details of valid signatures.

### Parameters

- `path`: The path to the directory to scan for files.

### Example

#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and display the details of valid signatures.

```powershell
.\get-authenticode-signatures.ps1 -path "C:\path\to\directory"
```

#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and export the details of valid signatures to a CSV file.

```powershell
.\get-authenticode-signatures.ps1 -path "C:\path\to\directory" | Export-Csv -Path "C:\path\to\output.csv" -NoTypeInformation
```
    
#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and display the unique SubjectName of valid signatures found.

```powershell
.\get-authenticode-signatures.ps1 -Path "C:\path\to\directory" | Select-Object -Property SubjectName -Unique 
```

#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and display the details of valid signatures with SubjectName containing "Microsoft".

```powershell
.\get-authenticode-signatures.ps1 -Path "C:\path\to\directory" | Where-Object { $_.SubjectName -like "*Microsoft*" }
```

#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and group the details of valid signatures by SubjectName.
```powershell
.\get-authenticode-signatures.ps1 -Path "C:\path\to\directory" | Group-Object -Property SubjectName
```    

#### This command will scan the specified directory for files with .exe, .dll, and .ps1 extensions and display the details of valid signatures with Thumbprint equals to "B9BC5E843979BF65A61713BE439D1409F60F6688".
```powershell
.\get-authenticode-signatures.ps1 -Path "C:\path\to\directory" | Where-Object {$_.Thumbprint -eq "B9BC5E843979BF65A61713BE439D1409F60F6688"
```
