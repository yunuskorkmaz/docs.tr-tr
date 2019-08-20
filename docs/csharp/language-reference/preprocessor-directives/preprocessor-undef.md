---
title: '#undef- C# başvuru'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605594"
---
# <a name="undef-c-reference"></a>#undef (C# Başvurusu)
`#undef`bir simge tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak ifade edilir `false`.  
  
 Bir sembol [#define](./preprocessor-define.md) yönergesi veya [-define](../compiler-options/define-compiler-option.md) derleyici seçeneği ile tanımlanabilir. Ayrıca `#undef` , yönergesi olmayan hiçbir deyimi kullanmadan önce yönerge dosyada görünmelidir.  
  
## <a name="example"></a>Örnek  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

**Hata ayıklama tanımlı değil**

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
