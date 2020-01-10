---
title: '#C# başvuru tanımla'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7457b05ae827675969398792bcb02f025f3028fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712591"
---
# <a name="define-c-reference"></a>#define (C# Başvurusu)
Bir sembol tanımlamak için `#define` kullanırsınız. [#İf](./preprocessor-if.md) yönergesine geçirilen ifade olarak sembolünü kullandığınızda, aşağıdaki örnekte gösterildiği gibi ifade `true`olarak değerlendirilir:  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> `#define` yönergesi, genellikle C ve C++' de yapıldığı gibi sabit değerleri bildirmek için kullanılamaz. İçindeki C# sabitler, bir sınıfın veya yapının statik üyeleri olarak en iyi şekilde tanımlanır. Bu tür sabitlere sahipseniz, bunları tutmak için ayrı bir "sabitler" sınıfı oluşturmayı düşünün.  
  
 Simgeler, derleme koşullarını belirtmek için kullanılabilir. Sembol için [#if](./preprocessor-if.md) ya da [#elif](./preprocessor-elif.md)ile test edebilirsiniz. Koşullu derleme gerçekleştirmek için <xref:System.Diagnostics.ConditionalAttribute> de kullanabilirsiniz.  
  
 Bir sembol tanımlayabilirsiniz, ancak bir simgeye değer atayamazsınız. Ayrıca Önişlemci yönergeleri olmayan yönergeleri kullanabilmeniz için `#define` yönergesinin dosyada görünmesi gerekir.  
  
 Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. [#Undef](./preprocessor-undef.md)bir simge tanımlayabilirsiniz.  
  
 `-define` veya `#define` ile tanımladığınız bir sembol aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.  
  
 `#define` kullanılarak oluşturulan bir simgenin kapsamı, simgenin tanımlandığı dosyadır.  
  
 Aşağıdaki örnekte gösterildiği gibi, dosyanın en üstüne `#define` yönergeleri koymanız gerekir.  
  
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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](./index.md)
- [const](../keywords/const.md)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
