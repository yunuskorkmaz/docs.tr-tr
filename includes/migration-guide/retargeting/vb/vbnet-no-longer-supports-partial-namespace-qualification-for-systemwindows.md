### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET kısmi ad niteliği System.Windows API'leri için artık desteklemektedir.

|   |   |
|---|---|
|Ayrıntılar|VB.NET projelerinde, .NET Framework 4.5.2 başlayarak, kısmen nitelenmiş ad alanları ile System.Windows API'leri belirtemezsiniz. Örneğin, başvurma <code>Windows.Forms.DialogResult</code> başarısız olur. Bunun yerine, kod için tam adı başvurması gerekir (<xref:System.Windows.Forms.DialogResult>) veya belirli bir ad alanı almak ve yalnızca çok başvurun <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Öneri|Kod başvurmak için güncelleştirilmesi gerektiğini <code>System.Windows</code> API'leri basit adları (ve ilgili ad alanı içe aktarma) veya tam olarak nitelenmiş adlar ile.|
|Kapsam|Küçük|
|Sürüm|4.5.2|
|Tür|Yeniden hedefleme|

