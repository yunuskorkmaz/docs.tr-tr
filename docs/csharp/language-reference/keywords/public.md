---
title: public (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 853f9c9ebe36345a897337d4e793d3c88059e068
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998733"
---
# <a name="public-c-reference"></a>public (C# Başvurusu)
`public` Anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir. Genel erişim, en esnek erişim düzeyidir. Bu örnekte olduğu gibi public üyelere erişmede hiçbir kısıtlama vardır:  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) daha fazla bilgi için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki sınıf bildirilen, `PointTest` ve `MainClass`. Genel üyeleri `x` ve `y` , `PointTest` doğrudan erişilir `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Değiştirirseniz `public` erişim düzeyi için [özel](../../../csharp/language-reference/keywords/private.md) veya [korumalı](../../../csharp/language-reference/keywords/protected.md), hata iletisi alırsınız:  
  
 'PointTest.y' koruma düzeyi nedeniyle erişilemez durumda.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)
