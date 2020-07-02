---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620609"
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
