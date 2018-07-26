### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>Page.LoadComplete olay artık System.Web.UI.WebControls.EntityDataSource denetimine veri bağlama çağırmasına neden olur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Web.UI.Page.LoadComplete> Artık olayına neden olmadan <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=name> denetiminin oluşturma/güncelleştirme/silme parametrelerine yönelik değişiklikler için veri bağlama çağırmasına. Bu değişiklik veritabanına fazlalık bir seyahat ortadan kaldırır, denetim değerlerinin sıfırlanmasını önler ve gibi diğer veri denetimleriyle tutarlı bir davranış üretir <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=name> ve <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=name>. Bu değişiklik uygulamaları içinde veri bağlamayı çağırmaya dayanması kurtarılamaz farklı davranış üretir <xref:System.Web.UI.Page.LoadComplete> olay.|
|Öneri|Veri bağlama için bir gereksinimi varsa, el ile databind sonrası arka planda önceki bir olayı çağırır.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

