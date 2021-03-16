---
description: '#tanımlama-C# başvurusu'
title: '#tanımlama-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: dddc60b99a55762ae26a470fcd6b6a0e9b98bcf8
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480362"
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
  
 Ayrıca, [**Definesabitleri**](../compiler-options/language.md#defineconstants) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. [#Undef](./preprocessor-undef.md)bir simge tanımlayabilirsiniz.  
  
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
