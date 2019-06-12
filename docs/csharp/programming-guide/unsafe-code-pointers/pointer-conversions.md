---
title: İşaretçi dönüşümleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833469"
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
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/operators/stackalloc.md)
