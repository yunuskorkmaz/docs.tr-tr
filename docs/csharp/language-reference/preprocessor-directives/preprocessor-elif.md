---
description: '#Elif-C# başvurusu'
title: '#Elif-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132293"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif` bileşik bir koşullu yönerge oluşturmanıza olanak sağlar. `#elif`Yukarıdaki [#if](./preprocessor-if.md) ne de önceki, isteğe bağlı bir yönerge ifadesi olarak değerlendiriliyorsa ifade değerlendirilir `#elif` `true` . Bir `#elif` ifade olarak değerlendirilirse `true` , derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir. Örneğin:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 `==`Birden çok sembolü değerlendirmek için İşleçleri (eşitlik), (eşitsizlik), ( `!=` `&&` ve) ve `||` (veya) kullanabilirsiniz. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif` , ile eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Kullanılması `#elif` daha basittir çünkü her biri `#if` bir [#endif](./preprocessor-endif.md)gerektirir, ancak bir `#elif` eşleştirme olmadan kullanılabilir `#endif` .  
  
 Öğesinin nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) `#elif` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
