---
title: '#If Önişlemci yönergesi- C# başvuru'
ms.custom: seodec18
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 561a628c60888a8d4f3c50c8413784e1ed210599
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035999"
---
# <a name="if-c-reference"></a>#if (C# Başvurusu)

C# Derleyici bir`#if`yönergesi ile karşılaştığında, sonunda bir [#endif](preprocessor-endif.md) yönergesi ile, yalnızca belirtilen sembol tanımlanmışsa, yönergeler arasındaki kodu derler. C ve C++' nin aksine, bir simgeye sayısal değer atayamazsınız. İçindeki C# #if deyimleri Boolean olur ve yalnızca sembolün tanımlanıp tanımlanmadığını sınar. Örneğin:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

Yalnızca [true](../keywords/true-literal.md) veya [false değerini](../keywords/false-literal.md)test etmek için [==](../operators/equality-operators.md#equality-operator-) (eşitlik) ve [! =](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) işleçlerini kullanabilirsiniz. Doğru, simgenin tanımlandığı anlamına gelir. Deyimin `#if DEBUG` `#if (DEBUG == true)`ile aynı anlamı vardır. İşleçlerini [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (ve), [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (veya) ve [!](../operators/boolean-logical-operators.md#logical-negation-operator-) (değil) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için. Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.

## <a name="remarks"></a>Açıklamalar

`#if`, [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleriyle birlikte, bir veya daha fazla simgenin varlığına göre kodu dahil etmenize veya dışlamanızı sağlar. Bu, hata ayıklama derlemesi için kod derlerken veya belirli bir yapılandırma için derlenirken yararlı olabilir.

`#if` yönergesiyle başlayan koşullu bir yönerge açıkça bir `#endif` yönergesi ile sonlandırılmalıdır.

`#define` bir simge tanımlamanızı sağlar. Sonra, `#if` yönergesine geçirilen ifade olarak sembolünü kullanarak, ifade `true`olarak değerlendirilir.

Ayrıca, [-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir simge tanımlayabilirsiniz. [#Undef](preprocessor-undef.md)bir simge tanımlayabilirsiniz.

`-define` veya `#define` ile tanımladığınız bir sembol aynı ada sahip bir değişkenle çakışmaz. Diğer bir deyişle, bir değişken adı bir Önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir Önişlemci yönergesi tarafından değerlendirilebilmelidir.

`#define` ile oluşturulan bir simgenin kapsamı tanımlandığı dosyadır.

Yapı sistemi, SDK stili projelerde farklı [hedef çerçeveleri](../../../standard/frameworks.md) temsil eden önceden tanımlanmış ön işlemci sembolleri de farkındadır. Birden fazla .NET uygulaması veya sürümü hedefleyebilir uygulamalar oluştururken faydalıdır.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Geleneksel .NET Framework projelerinde, Visual Studio 'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin Özellikler sayfaları aracılığıyla el ile yapılandırmanız gerekir.

Önceden tanımlanmış diğer semboller, hata ayıklama ve Izleme sabitlerini içerir. `#define`kullanarak proje için ayarlanan değerleri geçersiz kılabilirsiniz. Örneğin, hata ayıklama sembolü, derleme yapılandırma özelliklerine ("hata ayıklama" veya "yayın" modu) göre otomatik olarak ayarlanır.

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
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
