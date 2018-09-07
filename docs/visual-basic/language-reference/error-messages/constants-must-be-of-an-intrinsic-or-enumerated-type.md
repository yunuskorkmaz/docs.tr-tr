---
title: Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 4d635d289ed99aed48c296c278bc546971af51da
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083928"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
Bir sınıf, yapı ya da dizi türü veya içeren bir genel türü tarafından tanımlanan bir tür parametresi olarak bir sabit bildirme girişiminde bulundunuz.  
  
 Sabitler iç bir türde olması gerekir (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, veya `UShort`), veya bir `Enum` türüne göre bir integral türleri.  
  
 **Hata Kimliği:** BC30424  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bir iç öğe olarak bir sabit bildirme veya `Enum` türü.  
  
2.  Bir sabit ayrıca özel bir değer gibi olabilir `True`, `False`, veya `Nothing`. Derleyici iç türü uygun olması için önceden tanımlanmış bu değerleri göz önünde bulundurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Veri Türleri](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
