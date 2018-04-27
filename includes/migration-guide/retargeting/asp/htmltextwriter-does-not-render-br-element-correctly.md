### <a name="htmltextwriter-does-not-render-br-element-correctly"></a>HtmlTextWriter işlemek değil `<br/>` öğesi doğru

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6, çağırma başlayarak <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ve <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> ile bir <code>&lt;BR /&gt;</code> öğesi doğru ekler tek <code>&lt;BR /&gt;</code> (iki yerine)|
|Öneri|Bir uygulama üzerinde ek bağlıysa <code>&lt;BR /&gt;</code> etiketi <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> ikinci kez çağrılmalıdır. Bu davranış değişikliği yalnızca .NET Framework 4.6 veya daha sonra eski davranışı alabilmek için .NET Framework'ün önceki sürümünü hedefleyecek şekilde başka bir seçenek olacak şekilde hedefleyen uygulamalar etkilediğini unutmayın.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|

