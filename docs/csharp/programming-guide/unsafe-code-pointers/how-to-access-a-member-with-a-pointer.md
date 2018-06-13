---
title: 'Nasıl yapılır: İşaretçiyle bir Üyeye Erişme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 20f0dd18bb5ca132d05335953958d8f747b6abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332208"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Nasıl yapılır: İşaretçiyle bir Üyeye Erişme (C# Programlama Kılavuzu)
Güvenli olmayan bir içerikte bildirilmiş bir yapı üyesi erişmek için üye erişimi işleci aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz `p` gösteren bir işaretçidir bir [yapısı](../../../csharp/language-reference/keywords/struct.md) üyesi içeren `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir [yapısı](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, iki koordinat içeren `x` ve `y` bildirilir ve örneği. Üye erişimi işleci kullanılarak `->` örneğini gösteren bir işaretçi `home`, `x` ve `y` değerler atanır.  
  
> [!NOTE]
>  Dikkat ifade `p->x` ifade eşdeğerdir `(*p).x`, ve iki ifadeye birini kullanarak aynı sonucu elde edebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi İfadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
