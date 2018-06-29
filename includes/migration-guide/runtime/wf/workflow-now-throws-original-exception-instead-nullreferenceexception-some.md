### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>İş akışı şimdi bazı durumlarda NullReferenceException yerine özgün özel durum oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ve önceki sürümlerinde, bir iş akışı etkinliği çalıştırma yöntemi ile bir durum oluşturduğunda bir <code>null</code> değerini <xref:System.Exception.Message> System.Activities iş akışı çalışma zamanı özelliği oluşturur bir <xref:System.NullReferenceException?displayProperty=name>, maskeleme Orijinal özel durumu. .NET Framework 4.7 önceden maskelenmiş özel durum oluşur.|
|Öneri|Kodunuzu üzerinde işleme dayalıysa <xref:System.NullReferenceException?displayProperty=name>, özel etkinliklerden oluşturulan özel durumları yakalamak şekilde değiştirin.|
|Kapsam|Küçük|
|Sürüm|4.7|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

