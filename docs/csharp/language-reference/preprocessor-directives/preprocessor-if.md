---
title: '#Önişlemci yönergesi - C# başvurusu'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: df1b26b0e06d4fff81627ec633ce97f9d6ca036f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239637"
---
# <a name="if-c-reference"></a>#if (C# Başvurusu)

C# derleyicisi karşılaştığında bir `#if` yönergesi, ardından sonuç ile bir [#endif](preprocessor-endif.md) yalnızca belirtilen simge tanımlanmışsa yönergesi, bu yönergeleri arasında kod derler. C ve C++'ın aksine, bir sembol için sayısal bir değer atanamaz. #İf deyiminde C#, Boole ve yalnızca veya sembol tanımlanmış olup olmadığını test eder. Örneğin:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

İşleçleri [ == ](../operators/equality-comparison-operator.md) (eşitlik) ve [! =](../operators/not-equal-operator.md) (yalnızca test etmek için eşitsizlik) [true](../keywords/true.md) veya [false](../keywords/false.md). Doğru simge tanımlanmadıysa anlamına gelir. Deyim `#if DEBUG` olarak aynı anlamı `#if (DEBUG == true)`. İşleçleri [ && ](../operators/conditional-and-operator.md) (ve) [ &#124; &#124; ](../operators/conditional-or-operator.md) (veya) ve [!](../operators/logical-negation-operator.md) (birden fazla sembol tanımlı olup olmadığını değerlendirmek için değil). Ayrıca, simgeler ve işleçler parantezli gruplandırabilirsiniz.

## <a name="remarks"></a>Açıklamalar

`#if`, birlikte [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), ve [#undef](preprocessor-undef.md) yönergeleri sağlar dahil veya kod üzerinde bir veya daha fazla sembolleri varlığını temel hariç tutabilirsiniz. Kod hata ayıklama derlemesi için derleme yaparken veya belirli bir yapılandırma için derleme yaparken bu yararlı olabilir.

Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça tamamlanmalıdır ile bir `#endif` yönergesi.

`#define` bir sembol tanımlamanızı sağlar. Ardından sembolü kullanmadan tarafından geçirilen ifade olarak `#if` yönergesi, ifadenin değerlendirdiği `true`.

Ayrıca bir simge tanımlayabilirsiniz [-tanımlama](../compiler-options/define-compiler-option.md) derleyici seçeneği. Sahip bir simge tanımlarını Kaldır [#undef](preprocessor-undef.md).

İle tanımladığınız bir sembol `-define` veya `#define` aynı ada sahip bir değişken çakışmadığından. Diğer bir deyişle, bir değişken adı bir önişlemci yönergesine geçmemiş olmalıdır ve bir simge yalnızca bir önişlemci yönergesince değerlendirilebilir.

İle oluşturulan bir simgenin kapsamı `#define` , tanımlandığı dosyadır.

Derleme sistemi de farklı temsil eden önceden tanımlanmış önişlemci sembolleri, farkındadır [hedef çerçeveyi](../../../standard/frameworks.md). Bunlar, birden fazla .NET uygulaması veya sürümü hedefleyen uygulamaları oluştururken kullanışlı.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Diğer önceden tanımlanmış semboller hata ayıklama ve izleme sabitleri içerir. Proje kullanmak için ayarlanan değerleri geçersiz kılabilirsiniz `#define`. Hata ayıklama sembolü, örneğin, yapı yapılandırması özelliklerini ("Debug" veya "Sürüm" modu) bağlı olarak otomatik olarak ayarlanır.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek bir dosya bir MYTEST sembolünü tanımlayın ve ardından MYTEST ve hata ayıklama sembolleri değerlerini test gösterilmektedir. Bu örnek çıktısı, proje hata ayıklama veya sürüm yapılandırma modunu olup oluşturulan bağlıdır.

```csharp
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

Aşağıdaki örnek, mümkün olduğunda, yeni API'leri kullanabilmek için farklı bir hedef çerçeveleri test işlemini göstermektedir:

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Ön İşlemci Yönergeleri](index.md)  
- [Nasıl yapılır: İzleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).
