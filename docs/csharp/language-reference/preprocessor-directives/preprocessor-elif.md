---
title: '#elif- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608590"
---
# <a name="elif-c-reference"></a>#elif (C# Başvurusu)
`#elif`bileşik bir koşullu yönerge oluşturmanıza olanak sağlar. Yukarıdaki #if ne de `#elif` önceki, isteğe bağlı bir [](./preprocessor-if.md) yönerge ifadesi olarak `true`değerlendiriliyorsa ifadedeğerlendirilir.`#elif` Bir `#elif` ifade olarak `true`değerlendirilirse, derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir. Örneğin:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Birden çok sembolü değerlendirmek için `==` işleçleri (eşitlik) `!=` , (eşitsizlik `&&` ), (ve) ve `||` (veya) kullanabilirsiniz. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#elif`, ile eşdeğerdir:  
  
```csharp
#else  
#if  
```  
  
 Kullanılması `#elif` daha basittir çünkü her biri `#if` bir [#endif](./preprocessor-endif.md)gerektirir, ancak bir `#elif` eşleştirme `#endif`olmadan kullanılabilir.  
  
 Öğesinin [](./preprocessor-if.md) nasıl kullanılacağına `#elif`ilişkin bir örnek için bkz. #if.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
