### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews AllowPaging özelliği true olarak ayarlanmış görünümü son sayfasında ayrılırken PageIndexChanging olayını ateşle

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatanın neden <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> bazen için tetiklenecek değil <xref:System.Web.UI.WebControls.GridView?displayProperty=name>etkinleştirdiyseniz s <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Öneri|Bu sorun .NET Framework 4.6 sabit ve .NET Framework'ün bu sürüme yükseltme tarafından desteklenebilir. Bir iş-geçici bir çözüm, uygulama herhangi bir açık BindGrid gerçekleştirebilir <code>Page_Load</code> Bu koşullar isabet ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> olan son sayfa ve son<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> farklı <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatif olarak, bu senaryo, sorun gösterilmemiştir gibi uygulama (yerine özel sayfalama), disk belleği izin verecek şekilde değiştirilebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

