---
description: '#tanımlama-C# başvurusu'
title: '#tanımlama-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 961c20c091a4a6d7da421d94500abd41d2d60a5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160508"
---
# <a name="define-c-reference"></a>#define (C# Başvurusu)

`#define`Bir sembol tanımlamak için kullanırsınız. [#İf](./preprocessor-if.md) yönergesine geçirilen ifade olarak sembolünü kullandığınızda, `true` Aşağıdaki örnekte gösterildiği gibi ifade olarak değerlendirilir.  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> `#define`Yönerge, genellikle C ve C++ ' da yapıldığı gibi sabit değerleri bildirmek için kullanılamaz. C# ' deki sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır. Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.  
  
 Simgeler, derleme koşullarını belirtmek için kullanılabilir. Sembol için [#if](./preprocessor-if.md) ya da [#elif](./preprocessor-elif.md)ile test edebilirsiniz. <xref:System.Diagnostics.ConditionalAttribute>Koşullu derleme gerçekleştirmek için öğesini de kullanabilirsiniz.  
  
 Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız. `#define`Ayrıca Önişlemci yönergeleri olmayan herhangi bir yönergeyi kullanmadan önce yönerge dosyada görünmelidir.  
  
 Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. [#Undef](./preprocessor-undef.md)bir simge tanımlayabilirsiniz.  
  
 Veya ile tanımladığınız bir sembol `-define` `#define` aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.  
  
 Kullanılarak oluşturulan bir simgenin kapsamı, `#define` sembolün tanımlandığı dosyadır.  
  
 Aşağıdaki örnekte gösterildiği gibi `#define` yönergeleri dosyanın en üstüne koymanız gerekir.  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 Bir simgenin nasıl tanımlanacağını gösteren bir örnek için bkz. [#undef](./preprocessor-undef.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)
- [const](../keywords/const.md)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
