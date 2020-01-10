---
title: '#elif- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712578"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif`, bileşik bir koşullu yönerge oluşturmanıza imkan tanır. `#elif` ifadesi, önceki [#if](./preprocessor-if.md) ne de önceki, isteğe bağlı `#elif` yönerge ifadelerinin `true`olarak değerlendirilmediği takdirde değerlendirilir. `#elif` bir ifade `true`değerlendirilirse, derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir. Örneğin:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Birden çok simgeyi değerlendirmek için `==` (eşitlik), `!=` (eşitsizlik), `&&` (ve) ve `||` (ya da) işleçlerini kullanabilirsiniz. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif` ile eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Her `#if` [#endif](./preprocessor-endif.md)gerektirdiğinden `#elif` kullanımı basittir, ancak bir `#elif` eşleşen bir `#endif`olmadan kullanılabilir.  
  
 `#elif`nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
