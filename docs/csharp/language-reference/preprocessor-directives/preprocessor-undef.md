---
title: '#undef- C# başvuru'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712448"
---
# <a name="undef-c-reference"></a>#undef (C# Başvurusu)
`#undef` bir sembol tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak, ifade `false`olarak değerlendirilir.  
  
 Bir sembol [#define](./preprocessor-define.md) yönergesi veya [-define](../compiler-options/define-compiler-option.md) derleyici seçeneği ile tanımlanabilir. Ayrıca, yönergesi olmayan deyimleri kullanmadan önce `#undef` yönergesinin dosyada görünmesi gerekir.  
  
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
