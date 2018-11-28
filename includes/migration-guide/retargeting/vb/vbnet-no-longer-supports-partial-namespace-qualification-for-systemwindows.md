### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET kısmi ad niteliği System.Windows API'leri için artık desteklemektedir.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2 başlayarak VB.NET projeleri System.Windows API'leri kısmen nitelenmiş ad alanları ile belirtemezsiniz. Örneğin, söz konusu <code>Windows.Forms.DialogResult</code> başarısız olur. Bunun yerine, kod tam adına başvurmak gerekir (<xref:System.Windows.Forms.DialogResult>) veya belirli ad alanını içeri aktarır ve başvurmak için yalnızca <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Öneri|Kod başvurmak için güncelleştirilmesi gerektiğini <code>System.Windows</code> API'leri basit adları (ve ilgili ad alanı alma) veya tam olarak nitelenmiş adlar.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Yeniden Hedefleme|

