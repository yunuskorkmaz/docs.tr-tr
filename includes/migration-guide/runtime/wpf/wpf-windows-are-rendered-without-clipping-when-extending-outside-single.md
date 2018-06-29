### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF windows kırpma olmadan tek bir izleyici dışında genişletirken işlenir

|   |   |
|---|---|
|Ayrıntılar|Birden çok monitör senaryosunda tek görüntüleme dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencereyi işlenir. Bu, tek bir görüntüleme genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.|
|Öneri|Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında ya da ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulama başlangıçta özelliği.|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|çalışma zamanı|

