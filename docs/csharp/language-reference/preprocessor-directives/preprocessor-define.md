---
title: "#(C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a>#define (C# Başvurusu)
Kullandığınız `#define` bir simge tanımlamak için. Geçirilen ifade olarak simgenin kullandığınızda [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ifade için yönerge, değerlendirecek `true`, aşağıdaki örnekte gösterildiği gibi:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  `#define` Yönergesi, genellikle C ve C++ gerçekleştirilir gibi sabit değerleri bildirmek için kullanılamaz. C# sabitleri en iyi sınıfta veya yapı statik üyeleri tanımlanır. Bu tür birkaç sabitleri varsa, bunları tutmak için ayrı bir "Sabitleri" sınıf oluşturmayı düşünün.  
  
 Simgeler, derleme için koşulları belirtmek için kullanılabilir. Ya da simgesiyle için test edebilirsiniz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Aynı zamanda `conditional` koşullu derleme gerçekleştirmek için öznitelik.  
  
 Bir simge tanımlayabilirsiniz, ancak bir sembol için bir değer atayamazsınız. `#define` Yönergesi de önişlemci yönergeleri olmayan herhangi bir yönerge kullanmadan önce dosyada görünmelidir.  
  
 Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği. İle bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışmayan. Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.  
  
 Kullanılarak oluşturulmuş bir simge kapsamını `#define` simgenin tanımlanmıştı dosyasıdır.  
  
 Aşağıdaki örnekte gösterildiği gibi konulmalıdır `#define` dosyanın üst kısmındaki yönergeleri.  
  
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
  
 Bir simge tanımlarını Kaldır konusunda bir örnek için bkz: [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
