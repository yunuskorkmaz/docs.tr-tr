---
ms.openlocfilehash: 6da589057cebfbf3f67a46b8d49d3a61f037c4c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622282"
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
