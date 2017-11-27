---
title: "#<a name=\"if-c-reference\"></a>varsa (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a>#if (C# Başvurusu)
C# Derleyici karşılaştığında bir `#if` yönergesi, ardından sonunda göre bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) yalnızca belirtilen simgeyi tanımlanırsa yönerge, bu kod yönergeleri arasında derlenir.  C ve C++ aksine, bir simgeye sayısal bir değer atayamazsınız; C# #if ifade Boolean ve yalnızca simgenin veya tanımlanmış olup olmadığını sınar. Örneğin,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 İşleçleri kullanabilirsiniz [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) (eşitlik) [! =](../../../csharp/language-reference/operators/not-equal-operator.md) (yalnızca sınamak için eşitsizlik) [true](../../../csharp/language-reference/keywords/true.md) veya [false](../../../csharp/language-reference/keywords/false.md) . TRUE simgenin tanımlanan anlamına gelir. Deyim `#if DEBUG` aynı anlamı taşır `#if (DEBUG == true)`. İşleçleri kullanabilirsiniz [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) (ve) [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (veya) ve [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (birden çok simgeleri tanımlı olup olmadığını değerlendirmek için değil). Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  
 `#if`, birlikte [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), ve [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) yönergeleri sağlar içerebilir veya bir veya daha fazla simgeleri varlığını göre kod dışlayabilirsiniz. Hata ayıklama derlemesi kodunu derlerken veya belirli bir yapılandırma için derleme sırasında bu yararlı olabilir.  
  
 Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça bitirilmelidir ile bir `#endif` yönergesi.  
  
 `#define`ifade olarak simgesi kullanarak geçirilecek şekilde bir simge tanımlamanıza olanak tanır `#if` ifade için yönerge, değerlendirecek `true`.  
  
 Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği. İle bir simge tanımlarını Kaldır [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).  
  
 İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışmayan. Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.  
  
 İle oluşturulmuş bir simge kapsamını `#define` onu tanımlandığı dosyasıdır.  
  
## <a name="example"></a>Örnek  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
 **Hata ayıklama ve MYTEST tanımlanır**  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# önişlemci yönergeleri](../../../csharp/language-reference/preprocessor-directives/index.md)
