---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665170"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Özel bir INCC koleksiyondan bir öğe kaldırılırken seçicide kilitlenme

|   |   |
|---|---|
|Ayrıntılar|Bir <code>T:System.InvalidOperationException</code> aşağıdaki senaryolarda oluşabilir:<ul><li>ItemsSource için bir <code>T:System.Windows.Controls.Primitives.Selector</code> özel uygulanışı ile koleksiyonudur <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Seçili öğeyi koleksiyondan kaldırılır.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Sahip <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (bilinmeyen bir konumu belirtir).</li></ul>Özel durumun çağrı yığını System.Windows.Threading.Dispatcher.VerifyAccess() System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject adresindeki System.Windows.DependencyObject.GetValue (DependencyProperty dp) konumunda başlar öğesi) uygulamanın birden fazla dağıtıcı iş parçacığı varsa bu özel durum .NET Framework 4.5 içinde ortaya çıkabilir. .NET Framework 4.7 tek bir dağıtıcı iş parçacığıyla uygulamalarında özel durumu oluşabilir. .NET Framework 4.7.1 olan sorun çözüldüğünde.|
|Öneri|.NET Framework 4.7.1 yükseltin.|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Çalışma zamanı|
