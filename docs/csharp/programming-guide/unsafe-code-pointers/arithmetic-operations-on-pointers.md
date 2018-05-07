---
title: İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: c40b125e42649093aa1f1fe860a3e8f5d2690359
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>İşaretçilerde Aritmetik İşlemler (C# Programlama Kılavuzu)
Aritmetik işleçler kullanarak bu konuda ele alınmıştır `+` ve **-** işaretçileri yönlendirebilir.  
  
> [!NOTE]
>  Void işaretçileri hiçbir aritmetik işlemler gerçekleştirilemiyor.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Ekleme ve çıkarma sayısal değerler için veya işaretçileri  
 Bir değer ekleyebilirsiniz `n` türü [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md) bir işaretçi için `p`, herhangi bir türde `void*`. Sonuç `p+n` eklemelerini kaynaklanan işaretçi `n * sizeof(p) to the address of p`. Benzer şekilde, `p-n` alanından çıkarılmasıyla elde edilen işaretçi `n * sizeof(p)` adresinden gelen `p`.  
  
## <a name="subtracting-pointers"></a>İşaretçileri çıkarma  
 Aynı türde işaretçileri çıkarın. Sonuç her zaman türüdür `long`. Örneğin, varsa `p1` ve `p2` türü işaretçileridir `pointer-type*`, ardından ifade `p1-p2` sonuçlanır:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Hiçbir özel durum, etki alanı işaretçinin aritmetik işlemin taşar ve sonucu uygulamasına bağlıdır, üretilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
 [İşaretçileri İşleme](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
