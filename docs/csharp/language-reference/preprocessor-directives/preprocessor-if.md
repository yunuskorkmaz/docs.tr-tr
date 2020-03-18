---
title: '#if önişlemci yönergesi - C# Referans'
ms.date: 10/27/2019
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: d047b88f202341a795834809d0b601706c30fcb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75899850"
---
# <a name="if-c-reference"></a>#if (C# referansı)

C# derleyicisi bir `#if` yönergeyle karşılaştığında ve ardından [bir #endif](preprocessor-endif.md) yönergesi takip ettiğinde, kodu yalnızca belirtilen sembol tanımlanırsa yönergeler arasında derler. C ve C++'ın aksine, bir sembole sayısal değer atamazsınız. `#if` C# ifadesi Boolean'dır ve yalnızca sembolün tanımlanıp tanımlanmadığını test edin. Örnek:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

[==](../operators/equality-operators.md#equality-operator-) İşleçleri (eşitlik) ve [!=](../operators/equality-operators.md#inequality-operator-) (eşitsizlik) yalnızca [bool](../builtin-types/bool.md) değerlerini `true` veya `false`. `true`sembolün tanımlandığı anlamına gelir. İfade `#if DEBUG` , `#if (DEBUG == true)`. [&& (ve)](../operators/boolean-logical-operators.md#conditional-logical-and-operator-)kullanabilirsiniz, [&#124;&#124; (veya)](../operators/boolean-logical-operators.md#conditional-logical-or-operator-), ve [! (değil)](../operators/boolean-logical-operators.md#logical-negation-operator-) birden çok sembolün tanımlanıp tanımlanmadığını değerlendirmek için işleçler. Sembolleri ve işleçleri parantez içinde de gruplayabilirsiniz.

## <a name="remarks"></a>Açıklamalar

`#if`, [#else,](preprocessor-else.md) [#elif,](preprocessor-elif.md) [#endif,](preprocessor-endif.md) [#define](preprocessor-define.md)ve [#undef](preprocessor-undef.md) yönergeleri yle birlikte, bir veya daha fazla sembolün varlığına bağlı olarak kod eklemenize veya hariç tutmanıza olanak tanır. Bu, hata ayıklama yapısı için kod derlerken veya belirli bir yapılandırma için derleme yaparken yararlı olabilir.

Bir `#if` yönergeyle başlayan koşullu bir yönerge, bir `#endif` yönergeyle açıkça sonlandırılmalıdır.

`#define`bir sembol tanımlamanızı sağlar. Daha sonra ifade `#if` yönergeye geçti olarak sembolü kullanarak, `true`ifade değerlendirir.

[-define](../compiler-options/define-compiler-option.md) derleyici seçeneğiyle bir sembol de tanımlayabilirsiniz. Bir sembolü [#undef](preprocessor-undef.md)ile tanımlayabilirsiniz.

Tanımladığınız `-define` veya tanımladığınız `#define` bir sembol, aynı ada sahip bir değişkenle çakışmaz. Diğer bir diğer adıyla, bir değişken adı bir önişlemci yönergesine geçirilmemelidir ve bir sembol yalnızca bir önişlemci yönergesi tarafından değerlendirilebilir.

Oluşturulan `#define` bir sembolün kapsamı, oluşturulduğu dosyadır.

Yapı sistemi, SDK tarzı projelerde farklı [hedef çerçeveleri](../../../standard/frameworks.md) temsil eden önceden tanımlanmış önişlemci sembollerinin de farkındadır. Birden fazla .NET uygulamasını veya sürümünü hedefleyen uygulamalar oluştururken kullanışlıdır.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

> [!NOTE]
> Geleneksel .NET Framework projeleri için, Visual Studio'daki farklı hedef çerçeveler için koşullu derleme sembollerini projenin özellikleri sayfaları üzerinden el ile yapılandırmanız gerekir.

Önceden tanımlanmış diğer semboller de BUG ve TRACE sabitlerini içerir. Proje için ayarlanan değerleri kullanarak `#define`geçersiz kılabilirsiniz. Örneğin HATA Ayıklama simgesi, yapı yapılandırma özelliklerinize ("Hata Ayıklama" veya "Sürüm" modu) bağlı olarak otomatik olarak ayarlanır.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, bir dosyada MYTEST simgesini nasıl tanımlayabileceğinizi ve ardından MYTEST ve Hata Ayıklama simgelerinin değerlerini nasıl sınadığınızı gösterir. Bu örneğin çıktısı, projeyi Hata Ayıklama veya Sürüm yapılandırma modunda oluşturup oluşturamadığınıza bağlıdır.

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

Aşağıdaki örnek, mümkün olduğunda daha yeni API'leri kullanabilmeniz için farklı hedef çerçeveleri nasıl sınadığınızı gösterir:

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

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önİşleme İşlemciler Direktifleri](index.md)
- [Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
