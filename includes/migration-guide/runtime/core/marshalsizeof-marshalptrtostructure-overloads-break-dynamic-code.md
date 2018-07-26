### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Dinamik kod Marshal.SizeOf ve Marshal.PtrToStructure aşırı yüklemeler Kes

|   |   |
|---|---|
|Ayrıntılar|Dinamik olarak yöntemlere bağlama .NET Framework 4.5.1 başlayarak <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (aracılığıyla, Windows PowerShell, IronPython veya C# dynamic anahtar sözcüğü, örneğin) sonuçlanabilir <code>MethodInvocationExceptions</code> nedeni bu yöntemlerin yeni aşırı yüklemeler olabilecek altyapılarının için belirsiz eklenmemiş.|
|Öneri|Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için komut dosyalarını güncelleştirin. Bu can genellikle yöntemleri türü parametreleri olarak açıkça atayarak Bitti <xref:System.Type>. Bkz: [bu bağlantıyı](https://support.microsoft.com/kb/2909958/) daha fazla ayrıntı ve nasıl örnekleri geçici sorun.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

