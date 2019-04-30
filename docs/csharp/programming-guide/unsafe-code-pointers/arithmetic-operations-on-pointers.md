---
title: -İşaretçilerde aritmetik işlemler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: bfa81bc926b4fe81455cecb88bc55f4dcd69268e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677899"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>İşaretçilerde aritmetik işlemler (C# Programlama Kılavuzu)
Aritmetik işleçler kullanarak bu konuda ele alınmıştır `+` ve `-` işaretçileri işlemek için.  
  
> [!NOTE]
>  Tüm void işaretçilerde aritmetik işlemler gerçekleştirilemiyor.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Ekleme ve çıkarma işaretçileri gelen veya sayısal değerler  
 Bir değer eklediğiniz `n` türü [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md) işaretçisi. Varsa `p` bir işaretçi türü `pointer-type*`, sonuç `p+n` eklemesini elde edilen işaretçi `n * sizeof(pointer-type)` adresine `p`. Benzer şekilde, `p-n` arasındaki çıkarma işleminin sonucu işaretçi `n * sizeof(pointer-type)` adresinden `p`.  
  
## <a name="subtracting-pointers"></a>Çıkarma işaretçileri  
 Ayrıca, aynı türde işaretçileri çıkarabilirsiniz. Sonucu her zaman türüdür `long`. Örneğin, varsa `p1` ve `p2` türünde işaretçiler `pointer-type*`, ifade `p1-p2` sonuçlanır:  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 Hiçbir özel durum, etki alanı işaretçinin aritmetik işlemi taşıyor ve sonuç uygulamasının bağlıdır, üretilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
- [İşaretçileri İşleme](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
