---
title: Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9039376fc4d1f67ca9b526e46eaf28a0b1a3943c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587489"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
Bir sınıf, yapı veya dizi türü veya içeren bir genel türü tarafından tanımlanan bir tür parametresi olarak bir sabit bildirme denediniz.  
  
 Sabitler iç bir türde olması gerekir (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, veya `UShort`), veya bir `Enum` tam sayı türlerinden birini temel türü.  
  
 **Hata Kimliği:** BC30424  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bir iç olarak sabit bildirme veya `Enum` türü.  
  
2.  Bir sabit da özel bir değer gibi olabilir `True`, `False`, veya `Nothing`. Derleyici iç uygun türde olması için bu önceden tanımlanmış değerler göz önünde bulundurur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Veri Türleri](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)
