---
title: "Anonim İşlevler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonim İşlevler (C# Programlama Kılavuzu)
Adsız bir işlev bir "satır içi" deyimi veya bir temsilci türü bekleniyor her yerde kullanılabilir ifade değil. Adlandırılmış bir temsilci başlatmak veya bir yöntem parametresi olarak adlandırılan temsilci türü yerine geçirmek için kullanabilirsiniz.  
  
 Aşağıdaki konular, ayrı ayrı ele alınan anonim işlevler iki tür vardır:  
  
-   [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Lambda ifadeleri ifade ağaçları ve temsilciler bağlanabilir.  
  
## <a name="the-evolution-of-delegates-in-c"></a>C# temsilciler evrimi  
 C# 1. 0'açıkça, başka bir yerde kodunda tanımlandığına bir yöntem ile başlatarak temsilcisi örneği oluşturdu. C# 2.0 kavramı anonim yöntemler, bir temsilci çağrısının yürütülebilecek Adlandırılmamış satır içi deyim blokları yazmak için bir yol olarak kullanıma sunuldu. C# 3.0 anonim yöntemler için kavram benzer, ancak daha açıklayıcı ve kısa lambda ifadeleri sunmuştur. Bu iki özellik topluca olarak bilinen *anonim işlevler*. Genel olarak, uygulamalar, hedef sürüm 3.5 ve sonraki [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] lambda ifadeleri kullanmanız gerekir.  
  
 Aşağıdaki örnek, C# 1.0 temsilci oluşturulması C# 3.0 evrimi gösterir:  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Deyimler, ifadeler ve işleçler](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [İfade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
