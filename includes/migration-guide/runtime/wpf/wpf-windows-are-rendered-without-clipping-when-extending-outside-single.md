### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows tek bir izleyici genişletme olduğunda kırpma olmadan işlenir

|   |   |
|---|---|
|Ayrıntılar|Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir. Bu, tek bir görüntü genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.|
|Öneri|Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında veya ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulamanın başlangıcında özelliği.|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Çalışma zamanı|

