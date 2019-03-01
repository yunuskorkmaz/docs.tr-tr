---
title: 'Nasıl yapılır: işaretçiyle - bir dizi öğesine erişme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 7b2991776ca032aa53111187a061835725cfe223
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965611"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Nasıl yapılır: işaretçiyle bir dizi öğesine erişme (C# Programlama Kılavuzu)

Güvenli olmayan bir bağlamda, bir öğedeki bir bellek işaretçi öğe erişimi, kullanarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

Köşeli ayraç ifadesi örtük olarak dönüştürülebilir olmalıdır `int`, `uint`, `long`, veya `ulong`. İşlemi `p[e]` eşdeğerdir `*(p+e)`. C ve C++ gibi işaretçi öğe erişimi işlemleri denetlemez hataları.

## <a name="example"></a>Örnek

Bu örnekte, bir karakter dizisine 123 bellek konumları ayrılır `charPointer`. Dizi küçük harfler ve büyük harfler iki görüntülemek için kullanılan [için](../../../csharp/language-reference/keywords/for.md) döngüleri.

Dikkat ifade `charPointer[i]` ifadesine eşdeğerdir `*(charPointer + i)`, ve iki ifadeden birini kullanarak aynı sonucu elde edebilirsiniz.

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

**Büyük harfler:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Küçük harfler:**  
**abcdefghijklmnopqrstuvwxyz**  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
