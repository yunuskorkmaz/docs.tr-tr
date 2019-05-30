---
ms.openlocfilehash: 51691ced3f05201f784ccdeffbc130e34748b7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379652"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>WPF DataTemplate öğeleri için UIA görülebilir

|   |   |
|---|---|
|Ayrıntılar|Daha önce <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri için UI Otomasyonu görünmez. UI Otomasyonu 4.5 içinde başlayarak, bu öğeleri algılar. Bu pek çok durumda kullanışlıdır ancak değil içeren UIA ağaçları bağımlı testleri bozabilir <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri.|
|Öneri|UI Otomasyonu testleri bu uygulamayı gerekebilir güncelleştirilmiş için UIA ağaç artık dahil olmak üzere daha önce görünmez hesaba <xref:System.Windows.DataTemplate?displayProperty=name> öğeleri. Örneğin, bazı öğeler birbirinin yanına olmasını beklediğiniz testleri artık daha önce görünmez UIA öğeleri arasında beklenecek gerekebilir. Veya yeni değerlerle UIA öğeleri gerekebilir için belirli sayıları veya dizinleri dayalı testler güncelleştirildi.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
