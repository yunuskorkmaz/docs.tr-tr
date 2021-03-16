---
description: '#undef-C# başvurusu'
title: '#undef-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: ecbf8f5793e70c7dd6e602a3992ee3783a76c7ca
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477983"
---
# <a name="undef-c-reference"></a>#undef (C# Başvurusu)

`#undef` bir simge tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak ifade edilir `false` .  
  
 Bir sembol [#define](./preprocessor-define.md) yönergesi veya [**definesabitleri**](../compiler-options/language.md#defineconstants) derleyici seçeneği ile tanımlanabilir. `#undef`Ayrıca, yönergesi olmayan hiçbir deyimi kullanmadan önce yönerge dosyada görünmelidir.  
  
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

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
