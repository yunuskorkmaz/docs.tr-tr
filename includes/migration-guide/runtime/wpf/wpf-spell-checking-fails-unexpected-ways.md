### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>WPF yazım denetimi beklenmeyen şekilde başarısız

|   |   |
|---|---|
|Ayrıntılar|Bu, birkaç WPF yazım denetleyicisi sorunları içerir:<ul><li>WPF yazım denetleyicisi bazen oluşturur <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>WPF yazım denetimi başarısız olan <xref:System.UnauthorizedAccessException> 'farklı bir kullanıcı olarak çalıştır' kullanarak uygulamaları başlatılan zaman</li><li>WPF yazım denetleyicisi yanlış Almanca 'Hausnummer' gibi bileşik sözcüklerin yazım hatalarını tanımlar.</li></ul>|
|Öneri|Sorun #1 - Bu .NET Framework 4.6.2 düzeltildiğini sorunu #2 - WPF yazım denetleyicisi 'farklı bir kullanıcı olarak çalıştır' kullanarak uygulamalar başlatıldığında, artık desteklenmiyor. .NET Framework 4.6.2 başlayarak, bu şekilde başlatılan uygulamalara artık beklenmedik bir şekilde kilitleniyor - bunun yerine yazım denetleyicisi sessiz bir şekilde devre dışı bırakılır. Sorun #3 - Bu .NET Framework 4.6.2 düzeltilmiştir.|
|Kapsam|Kenar|
|Sürüm|4.6.1|
|Tür|çalışma zamanı|

