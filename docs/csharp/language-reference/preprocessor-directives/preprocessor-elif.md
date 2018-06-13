---
title: '#elif (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: ecc5c4b48790d0cb6825883922f3903414bb2b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275583"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif` Bileşik koşullu yönergesi oluşturmanızı sağlar. `#elif` Ne ifade'nin değerlendirilmesi önceki [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ya da herhangi bir önceki, isteğe bağlı, `#elif` yönerge ifadeleri değerlendirmek için `true`. Varsa bir `#elif` ifadeyi hesaplar için `true`, tüm kod arasında derleyici değerlendirir `#elif` ve sonraki koşullu yönergesi. Örneğin:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 İşleçleri kullanabilirsiniz `==` (eşitlik) `!=` (eşitsizlik) `&&` (ve) ve `||` (veya) çoklu sembolleri değerlendirmek için. Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif` kullanmakla eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Kullanarak `#elif` basittir, çünkü her `#if` gerektiren bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), ancak bir `#elif` eşleşen olmadan kullanılabilir `#endif`.  
  
 Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#elif`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
