### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Bir özelliğe genel olmayan ayarlayıcı ile iki yönlü veri bağlama desteklenmiyor

|   |   |
|---|---|
|Ayrıntılar|Genel bir Ayarlayıcısı olmadan bir özelliğine veri bağlama girişimi desteklenen bir senaryo olmamıştı. .NET Framework 4.5.1 başlayarak, bu senaryo oluşturmaz bir <xref:System.InvalidOperationException?displayProperty=name>. Bu yeni özel durum, özellikle .NET Framework 4.5.1'i hedefleyen uygulamalar için yalnızca oluşturulur unutmayın. Bir uygulamayı .NET Framework 4.5 hedefliyse, çağrı izin verilir. Uygulama belirli bir .NET Framework sürümünü hedef almıyor, bağlama tek yönlü olarak kabul edilir.|
|Öneri|Uygulama, tek yönlü bağlamaya kullanabilir veya özelliğin Ayarlayıcısı genel olarak kullanıma sunmak için güncelleştirilmesi gerekir. Alternatif olarak, .NET Framework 4.5 hedefleyen, uygulamanın eski davranışlar neden olur.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

