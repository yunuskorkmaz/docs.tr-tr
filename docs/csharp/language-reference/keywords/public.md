---
title: public (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="public-c-reference"></a>public (C# Başvurusu)
`public` Sözcüktür türleri ve tür üyeleri için bir erişim değiştiricisi. Genel erişim en fazla izne sahip erişim düzeyi değil. Bu örnekte olduğu gibi ortak üyelere erişme hiçbir kısıtlamaları vardır:  
  
```csharp  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
