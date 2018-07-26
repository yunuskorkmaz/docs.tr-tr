### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a>GridViews AllowPaging özelliği true olarak ayarlanmış son sayfa görünümün ayrılırken PageIndexChanging olayını ateşle

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatanın neden <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=name> bazen için değil ateşlenmesine <xref:System.Web.UI.WebControls.GridView?displayProperty=name>etkinleştirdiyseniz s <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=name>.|
|Öneri|Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir. Geçici çözüm, uygulama, herhangi bir açık BindGrid gerçekleştirebilir <code>Page_Load</code> Bu koşullar isabet ( <xref:System.Web.UI.WebControls.GridView?displayProperty=name> olan son sayfasında ve son<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name> farklıdır <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=name>). Alternatif olarak, bu senaryo, sorun gösterilmemiştir gibi uygulama disk belleği (yerine özel sayfalamayı) izin verecek şekilde değiştirilebilir.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|

