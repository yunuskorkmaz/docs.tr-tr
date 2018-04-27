### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference görevi şimdi yanlış mimarisiyle bağımlılıklar sizi uyarır.

|   |   |
|---|---|
|Ayrıntılar|Görev bir başvuru veya bağımlılıklarından biri uygulamanın mimarisi eşleşmediğini gösterir MSB3270 bir uyarı gösterir. Örneğin, bu ile derlenen bir uygulama ortaya çıkar <code>AnyCPU</code> seçeneği içeren bir x86 başvuru. Böyle bir senaryo çalışma zamanında bir uygulama hatasına neden (Bu durumda, uygulamayı bir x64 dağıttıysanız işlem).|
|Öneri|İki etki alanları şunlardır:<ul><li>Yeniden derleme uygulama MSBuild önceki bir sürümünü altında derlendiğinde görülmedi uyarılar oluşturur. Uyarı çalışma zamanı hatası olası kaynağı tanımladığından, ancak, araştırılan ele ve.</li><li>Uyarıları hata olarak kabul edilir, uygulama derlemek başarısız olur.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

