### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>ICommand.CanExecuteChanged olay davranışa .NET 4. 5 ' değiştirildi

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 içinde bir <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> olayı nesnesi olarak aynı nesne olay gönderen olduğu sürece yoksayıldı. Bu hata, .NET Framework 4. 5 ' güncelleştirmeleri bakım giderilmiştir.|
|Öneri|Bu hata, .NET Framework güncel olduğundan emin olun veya .NET Framework 4.5.1 yükselterek önlenebilir şekilde sürümler, Bakım .NET Framework 4. 5 ' düzeltilmiştir. Alternatif olarak, uygulama kodu kullanarak <xref:System.Windows.Input.ICommand?displayProperty=name> emin olmak için değiştirilebilir oluşturma zaman gönderen bir <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> komut olayı tetiklenmeden nesnesi ile aynı olur.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|Çözümleyiciler|<ul><li>CD0084</li></ul>|

