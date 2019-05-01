---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664969"
---
### <a name="chained-popups-with-staysopenfalse"></a>Açılan pencereler StaysOpen ile zincirleme = False

|   |   |
|---|---|
|Ayrıntılar|Açılır penceresi ile StaysOpen = False dışında açılan tıkladığınızda kapatmak gereken. Ne zaman iki veya daha fazla tür açılan pencereler zincirleme (yani birini içeren başka bir) dahil olmak üzere birçok ilgili sorunlar vardı:<ul><li>İki düzeyi'ni açın, P2 dışında fakat P1 içine tıklayın.  Hiçbir şey olmaz.</li><li>İki düzeyi açın, dış P1'a tıklayın.  Her iki açılan pencereleri kapatın.</li><li>Açma ve kapama iki düzeyi.  Ardından, P2 yeniden açmayı deneyin.  Hiçbir şey olmaz.</li><li>Üç düzeyden açmayı deneyin.  Şunları yapamazsınız.  (Hiçbir şey olmaz veya tıklattığınız bağlı olarak ilk iki düzey kapatın.) Bu gibi durumlarda (ve diğer çeşitleri) artık beklendiği gibi çalışmayabilir.</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
