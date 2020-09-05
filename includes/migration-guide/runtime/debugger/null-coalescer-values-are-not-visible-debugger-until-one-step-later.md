---
ms.openlocfilehash: af8de731ee93d0bfb01042d894f5730570dcdd78
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496718"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null birleştirme değerleri, bir adım daha sonra bir adımla hata ayıklayıcıda görünmez

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' deki bir hata, çerçevenin 64 bit sürümünde çalışırken atama işlemi yürütüldükten hemen sonra, null birleştirme işlemi yoluyla ayarlanan değerlerin hata ayıklayıcıda görünür olmasına neden olur.

#### <a name="suggestion"></a>Öneri

Hata ayıklayıcıda ek bir zaman adımlamak, yerel/alanın değerinin doğru güncelleştirilmesini sağlar. Ayrıca, bu sorun 4,6 .NET Framework düzeltilmiştir; Framework 'ün bu sürümüne yükseltmek sorunu çözmelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
