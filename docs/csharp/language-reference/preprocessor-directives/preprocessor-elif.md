---
title: "#elif (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif`Bileşik koşullu yönergesi oluşturmanızı sağlar. `#elif` Ne ifade'nin değerlendirilmesi önceki [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ya da herhangi bir önceki, isteğe bağlı, `#elif` yönerge ifadeleri değerlendirmek için `true`. Varsa bir `#elif` ifadeyi hesaplar için `true`, tüm kod arasında derleyici değerlendirir `#elif` ve sonraki koşullu yönergesi. Örneğin:  
  
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
 `#elif`kullanmakla eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Kullanarak `#elif` basittir, çünkü her `#if` gerektiren bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), ancak bir `#elif` eşleşen olmadan kullanılabilir `#endif`.  
  
 Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#elif`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
