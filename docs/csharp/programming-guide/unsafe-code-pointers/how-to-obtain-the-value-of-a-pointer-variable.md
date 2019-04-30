---
title: 'Nasıl yapılır: - işaretçi değişkeninin değerini edinme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677992"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Nasıl yapılır: işaretçi değişkeninin değerini edinme (C# Programlama Kılavuzu)

İşaretçi yöneltme işleci için bir işaretçi tarafından işaret edilen konumda bir değişkeni almak için kullanın. İfade, aşağıdaki biçimi alır burada `p` bir işaretçi türü:  

```csharp
*p;  
```

İşaretçi türünün dışındaki herhangi bir türde bir ifade üzerinde birli yöneltme işlecini kullanamazsınız. Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.  

Yöneltme işleci uygulandığında bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.  

## <a name="example"></a>Örnek

Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçiler kullanılarak erişilebilir. Unutmayın adresini `theChar` gelen çalıştıracak çalışma için bir değişkene ayrılan fiziksel adresi geçebileceğiniz farklılık gösterir.  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
**TheChar değerini Z =**  
**TheChar adresini 12F718 =**  
**PChar değerini Z =**  
**PInt değerini 90 =**  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
