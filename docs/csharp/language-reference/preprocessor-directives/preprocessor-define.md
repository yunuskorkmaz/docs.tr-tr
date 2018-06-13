---
title: '#(C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 1903b96de5f9dfa4efc252897a4a4bd18ed64924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286740"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
