---
title: '#undef (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 870b78580e5350f06fae33f2ac107dc3968b2c6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273416"
---
# <a name="undef-c-reference"></a>#undef (C# Başvurusu)
`#undef` bir simge tanımlarını Kaldır olanak tanır şekilde simgenin ifade olarak kullanarak, bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ifade için yönerge, değerlendirecek `false`.  
  
 Bir simge olabilir ile tanımlanmış [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) yönergesi veya [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği. `#undef` Yönergesi de yönergeleri olmayan deyimleri kullanmadan önce dosyada görünmelidir.  
  
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
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
