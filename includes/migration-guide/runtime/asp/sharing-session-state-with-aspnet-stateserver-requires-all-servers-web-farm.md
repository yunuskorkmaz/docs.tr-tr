### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>Oturum durumu Asp.Net StateServer ile paylaşımı aynı .NET Framework sürümünü kullanmak için web grubundaki tüm sunucuların gerektirir

|   |   |
|---|---|
|Ayrıntılar|Etkinleştirilirken <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> oturum durumunu, tüm verilen web grubundaki sunucular aynı sürüm .NET Framework'ün durumu için sırayla düzgün paylaşılan için kullanmalısınız.|
|Öneri|.NET Framework sürümleri aynı anda durumunu paylaşan web sunucularındaki yükseltme emin olun.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|

