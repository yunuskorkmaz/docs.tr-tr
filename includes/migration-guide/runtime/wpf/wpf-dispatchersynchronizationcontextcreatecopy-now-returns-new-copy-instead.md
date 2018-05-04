### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy artık geçerli örnek yerine yeni bir kopya döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4'te <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> performansı iyileştirme olarak öncelikle geçerli örneğine başvuru döndürdü. .NET Framework 4.5 mümkün eşit başvuruları doğru eşitleme bağlamındaki yürütülen parçacığıdır belirtmek sonuçlandırmak ilk kez yeni bir örneğini döndürür.  Bu başvuruları kimliğini denetler kod etkileneceğini, olası değil ancak değişikliği nedeniyle çağıran kodu <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> geçiş .NET Framework 4.5 veya daha yeni bir parçası olarak test edilmelidir.|
|Öneri|Unutmayın, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> artık yeni bir döndürülecek <xref:System.Threading.SynchronizationContext?displayProperty=name> nesnesi. Daha önce bu şekilde oluşturulan başvuruları eşdeğer kullanılan kod gerçekte, uygun bağlamda olsa da, .NET Framework 4.5 karşı ya da daha sonra oluşturulmuş yapar olup olmadığını denetlenirken değil.  Olası sorunlara neden karşın, etkilenen kod yolları kullanan bu herhangi bir sorun oluşturur belirlemek için yeterli olmalıdır.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|

