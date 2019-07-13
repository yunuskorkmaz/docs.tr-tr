---
ms.openlocfilehash: 2bb40294685c987de84138ee889e6b88f7184bb0
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857262"
---
### <a name="chained-popups-with-staysopenfalse"></a>Açılan pencereler StaysOpen ile zincirleme = False

|   |   |
|---|---|
|Ayrıntılar|Açılır penceresi ile StaysOpen = False dışında açılan tıkladığınızda kapatmak gereken. Ne zaman iki veya daha fazla tür açılan pencereler zincirleme (yani birini içeren başka bir) dahil olmak üzere birçok ilgili sorunlar vardı:<ul><li>İki düzeyi'ni açın, P2 dışında fakat P1 içine tıklayın.  Hiçbir şey olmaz.</li><li>İki düzeyi açın, dış P1'a tıklayın.  Her iki açılan pencereleri kapatın.</li><li>Açma ve kapama iki düzeyi.  Ardından, P2 yeniden açmayı deneyin.  Hiçbir şey olmaz.</li><li>Üç düzeyden açmayı deneyin.  Şunları yapamazsınız.  (Hiçbir şey olmaz veya tıklattığınız bağlı olarak ilk iki düzey kapatın.) Bu gibi durumlarda (ve diğer çeşitleri) artık beklendiği gibi çalışmayabilir.</li></ul>|
|`Scope`|Kenar|
|Version|4.7.1|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

