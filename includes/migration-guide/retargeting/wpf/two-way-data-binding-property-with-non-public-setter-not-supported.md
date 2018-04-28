### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Genel olmayan ayarlayıcı sahip bir özellik için iki yönlü veri bağlama desteklenmiyor

|   |   |
|---|---|
|Ayrıntılar|Ortak bir Ayarlayıcısı olmayan bir özellik için veri bağlama girişimi, desteklenen bir senaryo asla olmuştur. .NET Framework 4.5.1 başlayarak, bu senaryo özel durum oluşturacak bir <xref:System.InvalidOperationException?displayProperty=name>. Bu yeni özel durum, özellikle .NET Framework 4.5.1 hedefleyen uygulamalar için yalnızca oluşturulacaktır unutmayın. Bir uygulamayı .NET Framework 4.5 hedefliyorsa, çağrı izin verilir. Uygulamanın belirli bir .NET Framework sürüm hedeflemiyor, bağlama tek yönlü olarak kabul edilir.|
|Öneri|Uygulama, tek yönlü bağlama kullanabilir veya özelliğin ayarlayıcı genel olarak kullanıma sunmak için güncelleştirilmesi gerekir. Alternatif olarak, .NET Framework 4.5 hedefleme uygulamanın eski davranışlar sergilemesine izin neden olur.|
|Kapsam|Küçük|
|Sürüm|4.5.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

