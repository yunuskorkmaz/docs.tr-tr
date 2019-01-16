---
title: 'Nasıl yapılır: işaretçiyle - bir dizi öğesine erişme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 59765dbcad6c28cf2ad9f3df2052df19cafd08f1
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307285"
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

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

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
