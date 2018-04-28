### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Zaman aşımı bağımsız değişkenlerle Task.WaitAll yöntemleri için davranış değiştirme

|   |   |
|---|---|
|Ayrıntılar|Task.WaitAll davranışı .NET 4.5.In .NET Framework 4, tutarsız bir şekilde davranan bu yöntemleri daha tutarlı hale getirildi. Zaman aşımı süresi bir veya daha fazla görev tamamlandı veya yöntem çağrısı önce iptal ise, yöntem belirtti bir <xref:System.AggregateException?displayProperty=name> özel durum. Hiçbir görev tamamlandı veya yöntem çağrısı önce iptal edildi, ancak bir veya daha fazla görev yöntemi çağrısından sonra bu durumları girilen zaman aşımı süresi, yöntem false döndürdü.<br/><br/>.NET Framework 4.5, bu yöntem aşırı artık herhangi bir görevi hala zaman aşımı aralığı süresi ve bunlar throw çalıştırıyorsanız return false bir <xref:System.AggregateException?displayProperty=name> yalnızca bir giriş görevi (onu önce veya sonra yöntem olmasına bakılmaksızın iptal edildiyse özel durumu Çağrı) ve diğer bir görevler çalışmaya devam eder.|
|Öneri|Varsa bir <xref:System.AggregateException?displayProperty=name> kod IsCanceled özelliği aracılığıyla aynı algılama yerine yapmalısınız çağrılan, WaitAll çağrıdan önce iptal edildi bir görev algılama yolu olarak yakalanan (örneğin:. Any(t =&gt; t.IsCanceled)) zaman aşımı önce tüm awaited görevler tamamladıysanız .NET 4.6 yalnızca bu durumda başlatıldıysa bu yana.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|

