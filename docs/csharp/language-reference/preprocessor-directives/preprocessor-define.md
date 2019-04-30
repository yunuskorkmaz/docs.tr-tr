---
title: '#tanımlama - C# başvurusu'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 3b543181e3d836226759e77f0d56ed3c3e57e7ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688702"
---
# <a name="define-c-reference"></a>#define (C# Başvurusu)
Kullandığınız `#define` simge tanımlamak için. Geçirilen ifade olarak sembol kullanırken [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi, ifade için değerlendirilecek olan `true`aşağıdaki örnekte gösterildiği gibi:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  `#define` Yönergesi, genellikle C ve C++ içinde olduğu gibi sabit değerler bildirmek için kullanılamaz. C# içinde sabitleri en iyi bir sınıfın veya yapının üyeleri statik olarak tanımlanır. Birkaç sabitiniz varsa, bunları tutmak için ayrı bir "Sabitler" sınıfı oluşturmayı göz önünde bulundurun.  
  
 Derleme koşullarını belirtmek için simgeler kullanılabilir. Sembolü ile ya da test [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md). Ayrıca <xref:System.Diagnostics.ConditionalAttribute> koşullu derleme yapılacak.  
  
 Bir simge tanımlayabilir ancak bir simgeye değer atayamazsınız. `#define` Önişlemci yönergesi de olmayan yönergeleri kullanmadan önce yönergesinin dosyada görünmesi gerekir.  
  
 Ayrıca bir simge tanımlayabilirsiniz [-tanımlama](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği. Sahip bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 İle tanımladığınız bir sembol `-define` veya `#define` aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir önişlemci yönergesine geçmemiş olmalıdır ve bir simge yalnızca bir önişlemci yönergesince değerlendirilebilir.  
  
 Kullanılarak oluşturulan bir simgenin kapsamı `#define` simgenin tanımlandığı dosyadır.  
  
 Aşağıdaki örnekte gösterildiği gibi yerleştirmelisiniz `#define` yönergelerini dosyanın üst.  
  
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
  
 Bir sembolün tanımını kaldırmaya ilişkin bir örnek için bkz. [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
- [const](../../../csharp/language-reference/keywords/const.md)
- [Nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
