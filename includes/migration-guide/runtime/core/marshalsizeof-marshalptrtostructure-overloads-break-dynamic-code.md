### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf ve Marshal.PtrToStructure aşırı dinamik kodu Böl

|   |   |
|---|---|
|Ayrıntılar|Yöntemlere dinamik olarak bağlama .NET Framework 4.5.1,'den başlayarak <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (üzerinden, Windows PowerShell, IronPython veya C# dinamik anahtar sözcüğü, örneğin) sonuçlanabilir <code>MethodInvocationExceptions</code> bu yöntemlerin yeni aşırı altyapılarının belirsiz olabilecek eklenmediğinden.|
|Öneri|Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için komut dosyaları güncelleştirin. Genellikle yöntemleri türü parametreleri olarak açıkça atama tarafından yapılır olabilir <xref:System.Type>. Bkz: [bu bağlantıyı](https://support.microsoft.com/kb/2909958/) daha fazla ayrıntı ve nasıl örnekleri için geçici çözüm sorun.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|çalışma zamanı|

