---
title: '#undef (C# Başvurusu)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989715"
---
# <a name="undef-c-reference"></a>#undef (C# Başvurusu)
`#undef` Bir sembolün tanımını olanak tanır şekilde sembol deyim olarak kullanarak, bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi, ifade için değerlendirilecek olan `false`.  
  
 Bir sembol olabilir ya da ile tanımlanan [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) yönergesi veya [-tanımlama](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği. `#undef` Yönergeleri de yer almayan herhangi bir deyim kullanmadan önce yönergesi dosyada görünmesi gerekir.  
  
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

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
