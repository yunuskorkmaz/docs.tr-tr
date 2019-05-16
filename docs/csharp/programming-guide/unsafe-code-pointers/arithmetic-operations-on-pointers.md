---
title: -İşaretçilerde aritmetik işlemler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b08f9dbf8137e483bd38a4f396732191598532cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635228"
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
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
- [İşaretçileri İşleme](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
