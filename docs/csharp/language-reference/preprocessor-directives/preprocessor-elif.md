---
title: '#elif (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c6d797b68ad03023d6101b20cacae6d828abe0c1
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753966"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif` bir bileşik koşullu yönergesi oluşturmanıza olanak sağlar. `#elif` Kullanılmazsa, ifade değerlendirilir önceki [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya hiçbir, isteğe bağlı, önceki `#elif` yönerge nevyhodnocovat için `true`. Varsa bir `#elif` ifadeyi hesaplar için `true`, derleyicinin kod arasında değerlendirir `#elif` ve sonraki koşullu yönergesi. Örneğin:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 İşleçleri `==` (eşitlik) `!=` (eşitsizlik) `&&` (ve) ve `||` (veya) birden çok sembolleri değerlendirilecek. Ayrıca, simgeler ve işleçler parantezli gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif` kullanmakla eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Kullanarak `#elif` basittir çünkü her `#if` gerektiren bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)bilgileriyse bir `#elif` eşleşmeyen kullanılabilir `#endif`.  
  
 Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#elif`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
