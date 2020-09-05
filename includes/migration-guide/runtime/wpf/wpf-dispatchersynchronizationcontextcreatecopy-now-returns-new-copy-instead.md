---
ms.openlocfilehash: a806107456a65a4919592da9535a2617f677cfe0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496681"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext. CreateCopy şimdi geçerli örnek yerine yeni bir kopya döndürüyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4 ' te, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> birincil olarak bir performans iyileştirmesi olarak geçerli örneğe bir başvuru döndürür. .NET Framework 4,5 ' de, ilk kez bu eşit başvuruları sonuçlandırma, yürütülen iş parçacığının doğru eşitleme bağlamında olduğunu belirten yeni bir örnek döndürür.  Bu başvuruların kimliğini denetleyen kodun etkileneceği, ancak değişiklik nedeniyle çağıran kod, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> .NET Framework 4,5 veya daha yeni bir sürüme geçişin bir parçası olarak test edilmelidir.

#### <a name="suggestion"></a>Öneri

<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy>Şimdi yeni bir nesne döndüren farkında olun <xref:System.Threading.SynchronizationContext?displayProperty=fullName> . Daha önce, bu şekilde oluşturulan başvuruların denklik olarak kullanıldığı kod gerçekten doğru bağlamda olup olmadığını denetmıyordu, ancak .NET Framework 4,5 veya üzeri bir sürümde oluşturulmuştur.  Soruna neden olma olasılığı düşüktür, etkilenen kod yollarının kullanılması bunun herhangi bir sorun olup olmadığını belirlemede yeterli olmalıdır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

-->
