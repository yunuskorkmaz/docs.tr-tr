---
title: İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: db809fa9e086351184adcac43d67f53e9456894c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777407"
---
# <a name="pointer-conversions-c-programming-guide"></a>İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
Aşağıdaki tablo, önceden tanımlanmış örtük işaretçi dönüşümleri gösterir. Örtük dönüştürmeleri yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.  
  
## <a name="implicit-pointer-conversions"></a>Örtük işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|void *|  
|null|Herhangi bir işaretçi türü|  
  
 Açık işaretçi dönüştürme dönüştürmeler, var olan herhangi bir örtük dönüştürmeyi atama ifadesini kullanarak gerçekleştirmek için kullanılır. Aşağıdaki tabloda, bu dönüştürmeleri gösterilmektedir.  
  
## <a name="explicit-pointer-conversions"></a>Açık işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|Herhangi bir işaretçi türü|  
|sbyte, byte, kısa, ushort, int, uint, long veya ulong|Herhangi bir işaretçi türü|  
|Herhangi bir işaretçi türü|sbyte, byte, kısa, ushort, int, uint, long veya ulong|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir işaretçi `int` işaretçisine dönüştürülür `byte`. İşaretçiyi en düşük adresli baytına değişkenin işaret dikkat edin. Ne zaman sırayla artırmanız boyutu en fazla sonuç `int` (4 bayt), kalan baytlar değişkenin görüntüleyebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Türler](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
