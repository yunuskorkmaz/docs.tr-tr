---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802564"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Özel bir INCC koleksiyonundan bir öğeyi kaldırırken Seçici'de kilitlenme

|   |   |
|---|---|
|Ayrıntılar|Aşağıdaki <code>T:System.InvalidOperationException</code> senaryoda bir oluşabilir:<ul><li>ItemsSource için <code>T:System.Windows.Controls.Primitives.Selector</code> özel bir uygulama ile <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>bir koleksiyondur.</li><li>Seçili öğe koleksiyondan kaldırılır.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (bilinmeyen bir konumu gösterir).</li></ul>Özel durum callstack System.Windows.Threading.Dispatcher.VerifyAccess() System.Windows.DependencyObject.GetValue(DependencyProperty dp) system.windows.controls.primitives.Selector.GetIsSelected(DependencyObject adresindebaşlar öğesi)Uygulamanın birden fazla Sevk irsaliyesi iş parçacığı varsa, bu özel durum .NET Framework 4.5'te oluşabilir. .NET Framework 4.7'de tek bir Sevk Irsaliyesi iş parçacığına sahip uygulamalarda da istisna oluşabilir. Sorun .NET Framework 4.7.1'de giderilmiştir.|
|Öneri|.NET Framework 4.7.1'e yükseltin.|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|
