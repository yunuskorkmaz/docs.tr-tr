---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496372"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Özel bir ıNC koleksiyonundan öğe kaldırılırken seçicide kilitlenme

#### <a name="details"></a>Ayrıntılar

<code>T:System.InvalidOperationException</code>Aşağıdaki senaryoda bir durum oluşabilir:<ul><li>A için ItemSource, <code>T:System.Windows.Controls.Primitives.Selector</code> özel bir uygulamasına sahip bir koleksiyondur <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> .</li><li>Seçili öğe koleksiyondan kaldırıldı.</li><li>, <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> =-1 ' dir (bilinmeyen bir konum olduğunu gösterir).</li></ul>Özel durumun çağrı yığını, System. Windows. Controls. basitler. Selector. getııselected (DependencyObject öğesi) konumundaki System. Windows. DependencyObject. Dispatcher. doğrulamaları yaccess () konumunda başlar. bu durum, uygulamanın birden fazla Dağıtıcı iş parçacığı varsa .NET Framework 4,5 ' de oluşabilir. .NET Framework 4,7 ' de, özel durum tek bir dağıtıcı iş parçacığı olan uygulamalarda da oluşabilir. Sorun .NET Framework 4.7.1 içinde düzeltildi.

#### <a name="suggestion"></a>Öneri

.NET Framework 4.7.1 ' ye yükseltin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
