---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621396"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen ile zincirleme açılan pencere = yanlış

#### <a name="details"></a>Ayrıntılar

Açılan pencerenin dışına tıkladığınızda StaysOpen = false içeren bir açılan pencere kapatılacak. İki veya daha fazla açılan pencere zincirleme olduğunda (yani bir diğeri içeriyorsa), aşağıdakiler dahil olmak üzere çok sayıda sorun oluştu:<ul><li>İki düzey açın, P2 dışını, ancak P1 içinde tıklayın.  Hiçbir şey olmaz.</li><li>İki düzey açın, P1 dış P1 öğesine tıklayın.  Her iki açılır pencere da kapanır.</li><li>İki düzeyi açın ve kapatın.  Sonra P2 açmayı yeniden deneyin.  Hiçbir şey olmaz.</li><li>Üç düzey açmayı deneyin.  Yapamazsınız.  (Hiçbir şey olmaz ya da ilk iki düzey, tıkladığınıza bağlı olarak kapanır.) Bu durumlar (ve diğer çeşitler) artık beklenen şekilde çalışır.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.7.1|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
