---
title: "Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)
İşaretçi indirection işleci değişkeni için bir işaretçi işaret konumda almak için kullanın. Şu biçimi ifade alır nerede `p` bir işaretçi türü:  
  
```  
*p;  
```  
  
 İşaretçi türünün dışında herhangi bir türde bir ifade birli indirection işleci kullanamazsınız. Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.  
  
 İndirection işleci uyguladığınızda bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçileri kullanılarak erişilir. Unutmayın adresi `theChar` bir değişkene ayrılan fiziksel adresi değişebildiğinden gelen çalıştırma için Çalıştır ' farklılık gösterir.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **TheChar değerini Z =**  
**TheChar adresini 12F718 =**  
**PChar değerini Z =**   
**PInt değerini 90 =**    
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [İşaretçi ifadeleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Türler](../../../csharp/language-reference/keywords/types.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
