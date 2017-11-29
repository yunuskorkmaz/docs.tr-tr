---
title: "public (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords: public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 197ef4a2a8544d439b0c34ec14bb7752b760ea06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="public-c-reference"></a>public (C# Başvurusu)
`public` Sözcüktür türleri ve tür üyeleri için bir erişim değiştiricisi. Genel erişim en fazla izne sahip erişim düzeyi değil. Bu örnekte olduğu gibi ortak üyelere erişme hiçbir kısıtlamaları vardır:  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) daha fazla bilgi için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki sınıf bildirilir, `PointTest` ve `MainClass`. Genel üyeler `x` ve `y` , `PointTest` doğrudan erişilen `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Değiştirirseniz `public` erişim düzeyini [özel](../../../csharp/language-reference/keywords/private.md) veya [korumalı](../../../csharp/language-reference/keywords/protected.md), hata iletisi alırsınız:  
  
 'PointTest.y' koruma düzeyi nedeniyle erişilemiyor.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Özel](../../../csharp/language-reference/keywords/private.md)  
 [korumalı](../../../csharp/language-reference/keywords/protected.md)  
 [İç](../../../csharp/language-reference/keywords/internal.md)
