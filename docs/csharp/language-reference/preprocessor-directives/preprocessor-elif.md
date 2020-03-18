---
title: '#elif - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712578"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif`bileşik koşullu yönerge oluşturmanıza olanak sağlar. İfade, `#elif` ne önceki [#if](./preprocessor-if.md) ne de önceki, isteğe `#elif` bağlı, yönerge `true`ifadeleri değerlendirilmezse değerlendirilecektir. Bir `#elif` ifade , `true`derleyici ve sonraki koşullu yönerge arasındaki `#elif` tüm kodu değerlendirirse. Örnek:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Birden çok sembolü `==` değerlendirmek için `!=` işleçleri `&&` (eşitlik), `||` (eşitsizlik), (ve) ve (veya) kullanabilirsiniz. Sembolleri ve işleçleri parantez içinde de gruplayabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif`kullanmaya eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Her `#elif` `#if` biri bir [#endif](./preprocessor-endif.md)gerektirdiğinden, `#elif` bir eşleneme `#endif`olmadan kullanılabilir.  
  
 Nasıl [#if](./preprocessor-if.md) kullanılacağına bir örnek `#elif`için #if bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
