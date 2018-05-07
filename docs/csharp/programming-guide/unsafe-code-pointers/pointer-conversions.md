---
title: İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-conversions-c-programming-guide"></a>İşaretçi Dönüşümleri (C# Programlama Kılavuzu)
Aşağıdaki tabloda önceden tanımlanmış örtük işaretçi dönüşümleri gösterir. Örtük dönüşümler yöntemi çağırma ve atama deyimleri dahil olmak üzere birçok durumda oluşabilir.  
  
## <a name="implicit-pointer-conversions"></a>Örtük işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|void *|  
|null|Herhangi bir işaretçi türü|  
  
 Açık işaretçi dönüştürme var olduğu örtük dönüştürme, bir cast ifadesi kullanarak dönüşümlerini gerçekleştirmek için kullanılır. Aşağıdaki tabloda bu dönüşümleri gösterir.  
  
## <a name="explicit-pointer-conversions"></a>Açık işaretçi dönüşümleri  
  
|Başlangıç|Bitiş|  
|----------|--------|  
|Herhangi bir işaretçi türü|Herhangi bir işaretçi türü|  
|sbyte, bayt, short, ushort, int, uint, uzun veya ulong|Herhangi bir işaretçi türü|  
|Herhangi bir işaretçi türü|sbyte, bayt, short, ushort, int, uint, uzun veya ulong|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir işaretçi `int` gösteren bir işaretçi dönüştürülür `byte`. İşaretçinin en düşük adresli bayta değişkenin işaret dikkat edin. Ne zaman, sırayla Artır boyutu kadar sonuç `int` (4 bayt), değişkenin kalan bayt sayısı görüntüleyebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
