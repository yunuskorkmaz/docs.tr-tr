---
title: '#If Önişlemci yönergesi- C# başvuru'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d0297094fbb8098b706cb8c6338fa123afc0753b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605693"
---
# <a name="if-c-reference"></a>#if (C# Başvurusu)

C# Derleyici bir `#if` yönergeyle karşılaştığında, sonunda bir [#endif](preprocessor-endif.md) yönergesi ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler. C ve C++' nin aksine, bir simgeye sayısal değer atayamazsınız. İçindeki C# #if deyimleri Boolean olur ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar. Örneğin:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Yalnızca [true](../keywords/true-literal.md) veya [false](../keywords/false-literal.md)için [==](../operators/equality-operators.md#equality-operator-) test etmek amacıyla işleçleri (eşitlik) ve [! =](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) kullanabilirsiniz. Doğru, simgenin tanımlandığı anlamına gelir. İfade `#if DEBUG` , ile `#if (DEBUG == true)`aynı anlama sahiptir. İşleçlerini [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (ve), [](../operators/boolean-logical-operators.md#logical-negation-operator-) [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (veya) ve kullanın. (değil) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.

## <a name="remarks"></a>Açıklamalar

`#if`[#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar. Bu, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.

`#if` Yönergeyle başlayan koşullu bir yönerge, açıkça bir `#endif` yönergeyle sonlandırılmalıdır.

`#define`bir sembol tanımlamanızı sağlar. Ardından, simgesini `#if` yönergeye geçirilen ifade olarak kullanarak ifade olarak `true`değerlendirilir.

Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. [#Undef](preprocessor-undef.md)bir simge tanımlayabilirsiniz.

`-define` Veya ile`#define` tanımladığınız bir sembol aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.

İle `#define` oluşturulan sembolün kapsamı, tanımlandığı dosyadır.

Yapı sistemi, farklı [hedef çerçeveleri](../../../standard/frameworks.md)temsil eden önceden tanımlanmış önişlemci sembolleri de farkındadır. Birden fazla .NET uygulaması veya sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Önceden tanımlanmış diğer semboller, hata ayıklama ve Izleme sabitlerini içerir. Kullanarak `#define`proje için ayarlanan değerleri geçersiz kılabilirsiniz. Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, bir dosya üzerinde MYTEST sembolünü nasıl tanımlacağınızı ve sonra MYTEST ve hata ayıklama simgelerinin değerlerini test etmek için size gösterir. Bu örneğin çıktısı, projeyi hata ayıklama veya sürüm yapılandırma modunda derdığınıza bağlıdır.

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

Aşağıdaki örnekte, mümkünse daha yeni API 'Leri kullanabilmeniz için farklı hedef çerçeveler için nasıl test yapılacağı gösterilmektedir:

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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Ön İşlemci Yönergeleri](index.md)
- [Nasıl yapılır: Izleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
