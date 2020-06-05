---
title: Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9e36b84252c3d8762308e95323b8e284977df8c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409770"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
Bir sabiti sınıf, yapı veya dizi türü olarak ya da içeren bir genel tür tarafından tanımlanan bir tür parametresi olarak bildirmeye çalıştınız.  
  
 Sabitler bir iç tür (,,,,,,,,,,,,,,,,,,,,,,, `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` veya `UShort` ) olmalıdır veya `Enum` integral türlerinden birini temel alan bir tür olmalıdır.  
  
 **Hata kimliği:** BC30424  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Sabiti bir iç veya tür olarak bildirin `Enum` .  
  
2. Bir sabit,, veya gibi özel bir değer de `True` olabilir `False` `Nothing` . Derleyici, bu önceden tanımlı değerleri uygun iç türden olacak şekilde değerlendirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabitler ve numaralandırmalar](../constants-and-enumerations.md)
- [Veri türleri](../../programming-guide/language-features/data-types/index.md)
- [Veri türleri](../data-types/index.md)
