---
title: 'Nasıl yapılır: - işaretçiyle bir üyeye erişme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 9762b9e2487c30b81b7ef6ae22827b64e3cb02e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677738"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Nasıl yapılır: işaretçiyle bir üyeye erişme (C# Programlama Kılavuzu)
Güvenli olmayan bir bağlamda bildirilen bir yapının bir üyesine erişmek için üye erişimi işleci aşağıdaki örnekte gösterildiği gibi kullanabileceğiniz `p` işaretçisidir bir [yapı](../../../csharp/language-reference/keywords/struct.md) üye içeren `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir [yapı](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, iki koordinat içeren `x` ve `y` bildirildi ve örneği. Üye erişimi işleci kullanarak `->` örneğine bir işaretçi `home`, `x` ve `y` değerler atanır.  
  
> [!NOTE]
>  Dikkat ifade `p->x` ifadesine eşdeğerdir `(*p).x`, ve iki ifadeden birini kullanarak aynı sonucu elde edebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Türler](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
