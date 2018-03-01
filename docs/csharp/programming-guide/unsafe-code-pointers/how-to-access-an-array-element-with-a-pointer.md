---
title: "Nasıl yapılır: İşaretçiyle bir Dizi Öğesine Erişme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 737c1d7fc0bc0a739de5c0a6cbc5dc09f813133e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Nasıl yapılır: İşaretçiyle bir Dizi Öğesine Erişme (C# Programlama Kılavuzu)
Güvenli olmayan bir bağlamda, bellekte bir öğe işaretçi öğesi erişimi kullanarak aşağıdaki örnekte gösterildiği gibi erişebilirsiniz:  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 Köşeli ayraçlar ifadesinde örtük olarak dönüştürülebilir `int`, `uint`, `long`, veya `ulong`. P [e] işlemi eşdeğerdir *(p+e). C ve C++ gibi işaretçi öğesi erişim out-of-bounds denetlemez hataları.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir karakter dizisi 123 belleğinden ayrılan `charPointer`. Dizi küçük harf ve büyük harfler iki görüntülemek için kullanılan [için](../../../csharp/language-reference/keywords/for.md) döngüler.  
  
 Dikkat ifade `charPointer[i]` ifade eşdeğerdir `*(charPointer + i)`, ve iki ifadeye birini kullanarak aynı sonucu elde edebilirsiniz.  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Büyük harfler:**  
**ABCÇDEFGĞHIİJKLMNOÖPRSŞTUÜVYZ**  
**Küçük harf:**  
**abcçdefgğhıijklmnoöprsştuüvyz**   
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi ifadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
