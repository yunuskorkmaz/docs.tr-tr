### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference görevi bağımlılıklarının yanlış mimarisi ile artık uyarır.

|   |   |
|---|---|
|Ayrıntılar|Görev bir başvurusu veya bağımlılıklarından biri uygulamanın mimarisi eşleşmediğini gösteren MSB3270 bir uyarı gönderir. Örneğin, bu ile derlenen bir uygulamayı ortaya çıkar <code>AnyCPU</code> seçeneği içeren bir x86 başvuru. Bu tür bir senaryonun çalışma zamanında bir uygulama hatasına neden (Bu durumda, uygulama bir x64 dağıtılırsa işlem).|
|Öneri|İki etki alanı vardır:<ul><li>Yeniden derleme MSBuild'ın önceki bir sürümünden altında uygulama derlendiğinde görülmedi uyarılar oluşturur. Uyarı, çalışma zamanı hatası olası kaynak tanımladığından, ancak, araştırılması ele ve.</li><li>Uyarıları hata olarak kabul edilir, uygulama derlemek başarısız olur.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|

