---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620711"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>WPF DataTemplate öğeleri artık UıA 'ye görünür

#### <a name="details"></a>Ayrıntılar

Daha önce, <xref:System.Windows.DataTemplate?displayProperty=fullName> öğeler UI Otomasyonu için görünmezdi. 4,5 ' den başlayarak UI Otomasyonu bu öğeleri algılar. Bu pek çok durumda kullanışlıdır, ancak öğeleri içermeyen UıA ağaçlarına bağlı testleri kesebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Bu uygulama için UI Otomasyon testlerinin, artık daha önce görünmeyen öğeler de dahil olmak üzere UIA ağacı için hesabınıza güncelleştirilmeleri gerekebilir <xref:System.Windows.DataTemplate?displayProperty=fullName> . Örneğin, bazı öğelerin yanında olması beklenen testlerin, artık arasında daha önce görünmeyen UıA öğelerini beklemesi gerekebilir. Veya UıA öğelerine yönelik belirli sayımlar veya dizinlere dayanan testler yeni değerlerle güncelleştirilmiş olabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|
