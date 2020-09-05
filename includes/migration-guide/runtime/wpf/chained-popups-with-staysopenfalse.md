---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497370"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen ile zincirleme açılan pencere = yanlış

#### <a name="details"></a>Ayrıntılar

Açılan pencerenin dışına tıkladığınızda StaysOpen = false içeren bir açılan pencere kapatılacak. İki veya daha fazla açılan pencere zincirleme olduğunda (yani bir diğeri içeriyorsa), aşağıdakiler dahil olmak üzere çok sayıda sorun oluştu:<ul><li>İki düzey açın, P2 dışını, ancak P1 içinde tıklayın.  Hiçbir şey olmaz.</li><li>İki düzey açın, P1 dış P1 öğesine tıklayın.  Her iki açılır pencere da kapanır.</li><li>İki düzeyi açın ve kapatın.  Sonra P2 açmayı yeniden deneyin.  Hiçbir şey olmaz.</li><li>Üç düzey açmayı deneyin.  Yönetemezsiniz.  (Hiçbir şey olmaz ya da ilk iki düzey, tıkladığınıza bağlı olarak kapanır.) Bu durumlar (ve diğer çeşitler) artık beklenen şekilde çalışır.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
