---
title: '#define - C# Referans'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173438"
---
# <a name="define-c-reference"></a>#define (C# Başvurusu)
Bir `#define` sembol tanımlamak için kullanın. Sembolü [#if](./preprocessor-if.md) yönergesine geçirilen ifade olarak kullandığınızda, ifade `true`aşağıdaki örnekte görüldüğü gibi aşağıdaki leri değerlendirecektir:  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Yönerge, `#define` c ve c++'da genellikle yapıldığı gibi sabit değerleri bildirmek için kullanılamaz. C#'daki sabitler en iyi sınıfın veya yapının statik üyeleri olarak tanımlanır. Bu tür birkaç sabitinvarsa, bunları tutmak için ayrı bir "Sabitler" sınıfı oluşturmayı düşünün.  
  
 Semboller derleme için koşulları belirtmek için kullanılabilir. #if [veya](./preprocessor-if.md) [#elif](./preprocessor-elif.md)ile sembol için test edebilirsiniz. Koşullu derleme <xref:System.Diagnostics.ConditionalAttribute> gerçekleştirmek için de kullanabilirsiniz.  
  
 Bir simge tanımlayabilirsiniz, ancak bir sembole değer atayamazsınız. Önişlemci `#define` yönergeleri olmayan yönergeleri kullanmadan önce yönerge nin dosyada görünmesi gerekir.  
  
 [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir sembol de tanımlayabilirsiniz. Bir sembolü [#undef](./preprocessor-undef.md)ile tanımlayabilirsiniz.  
  
 Tanımladığınız `-define` veya tanımladığınız `#define` bir sembol, aynı ada sahip bir değişkenle çakışmaz. Diğer bir diğer adıyla, bir değişken adı bir önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir önişlemci yönergesi tarafından değerlendirilebilir.  
  
 Kullanılarak `#define` oluşturulan bir sembolün kapsamı, sembolün tanımlandığı dosyadır.  
  
 Aşağıdaki örnekte de görüldüğü `#define` gibi, yönergeleri dosyanın en üstüne koymanız gerekir.  
  
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
  
 Bir sembolün nasıl tanımlanabildiğini anlatan bir örnek için bkz. [#undef.](./preprocessor-undef.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](./index.md)
- [const](../keywords/const.md)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
