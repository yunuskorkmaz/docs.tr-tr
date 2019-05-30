---
ms.openlocfilehash: ff4d67a1c821fc96130c4efbd88eb5c56766da06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379684"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy artık geçerli örneği yerine yeni bir kopyasını döndürür

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4'te <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> öncelikle bir performans iyileştirme olarak geçerli örneğe bir başvuru döndürdü. .NET Framework 4.5, eşit başvuruların, yürütülen iş parçacığının doğru eşitleme bağlamıdır göstermesini sonuçlandırmak ilk kez mümkün hale getiren yeni bir örneğini döndürür.  Bu başvuruları kimliğini denetleyen kod etkileneceğini, beklenmez, ancak değişiklik nedeniyle, çağıran kod <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> geçiş .NET Framework 4.5 veya sonraki bir parçası olarak test edilmelidir.|
|Öneri|Unutmayın, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> artık yeni bir döndüreceği <xref:System.Threading.SynchronizationContext?displayProperty=name> nesne. Daha önce bu şekilde oluşturulan başvuruları denklik kullanılan kodu gerçekten doğru bağlamda oldu, ancak karşı .NET Framework 4.5 veya üzeri yapılandırıldığında mu olup olmadığını denetlenirken değil.  Olası sorunlara neden karşın, etkilenen kod yollarını uygulanması bu herhangi bir sorun paylaşılmamasını belirlemek için yeterli olması gerekir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
