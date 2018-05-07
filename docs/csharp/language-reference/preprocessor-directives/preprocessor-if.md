---
title: '#varsa önişlemci yönergesi (C# Başvurusu)'
ms.date: 02/13/2017
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 2ae0af6971dbf549b52e8168e035d8582bdab61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="if-c-reference"></a>#if (C# Başvurusu)

C# Derleyici karşılaştığında bir `#if` yönergesi, ardından sonunda göre bir [#endif](preprocessor-endif.md) yalnızca belirtilen simgeyi tanımlanırsa yönerge, bu yönergeleri arasında yer alan kodunu derler. C ve C++ aksine, bir simgeye sayısal bir değer atayamazsınız. C# #if ifade Boolean ve yalnızca simgenin veya tanımlanmış olup olmadığını sınar. Örneğin:

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

İşleçleri kullanabilirsiniz [ == ](../operators/equality-comparison-operator.md) (eşitlik) ve [! =](../operators/not-equal-operator.md) (yalnızca sınamak için eşitsizlik) [true](../keywords/true.md) veya [false](../keywords/false.md). TRUE simgenin tanımlanan anlamına gelir. Deyim `#if DEBUG` aynı anlamı taşır `#if (DEBUG == true)`. İşleçleri kullanabilirsiniz [ && ](../operators/conditional-and-operator.md) (ve) [ &#124; &#124; ](../operators/conditional-or-operator.md) (veya) ve [!](../operators/logical-negation-operator.md) (birden çok simgeleri tanımlı olup olmadığını değerlendirmek için değil). Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.

## <a name="remarks"></a>Açıklamalar

`#if`, birlikte [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), ve [#undef](preprocessor-undef.md) yönergeleri sağlar içerebilir veya bir veya daha fazla simgeleri varlığını göre kod dışlayabilirsiniz. Hata ayıklama derlemesi kodunu derlerken veya belirli bir yapılandırma için derleme sırasında bu yararlı olabilir.

Koşullu bir yönerge başlayarak bir `#if` yönergesi açıkça bitirilmelidir ile bir `#endif` yönergesi.

`#define` bir simge tanımlamanıza olanak sağlar. Geçirilen ifade olarak simgesini kullanarak tarafından `#if` için yönerge, ifadeyi hesaplar `true`.

Ayrıca, bir simge ile tanımlayabilirsiniz [/ define](../compiler-options/define-compiler-option.md) derleyici seçeneği. İle bir simge tanımlarını Kaldır [#undef](preprocessor-undef.md).

İle tanımlayan bir sembol `/define` veya `#define` aynı ada sahip bir değişken çakışan değil. Diğer bir deyişle, önişlemci yönergesi için bir değişken adı geçirilmemelidir ve bir simge yalnızca önişlemci yönergesi değerlendirilebilir.

İle oluşturulmuş bir simge kapsamını `#define` onu tanımlandığı dosyasıdır.

Derleme Sistemi aynı zamanda farklı temsil eden önceden tanımlanmış önişlemci simgeleri bilmez [hedef çerçeveler](../../../standard/frameworks.md). Birden fazla .NET uygulama veya sürüm hedefleyebilirsiniz uygulamaları oluştururken yararlı oldukları.

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

Diğer önceden tanımlanmış semboller hata ayıklama ve izleme sabitleri içerir. Proje kullanmak için ayarlanan değerlerle geçersiz kılabilirsiniz `#define`. Hata ayıklama simgesi, örneğin, yapı yapılandırma özelliklerini ("Hata ayıklama" veya "Yayın" modu) bağlı olarak otomatik olarak ayarlanır.

## <a name="examples"></a>Örnekler

Aşağıdaki örnekte bir dosyada MYTEST sembolünü tanımlayın ve MYTEST ve hata ayıklama simgeleri değerlerini test gösterilmektedir. Bu örnek çıktı projenin hata ayıklama veya yayın yapılandırma modunu olup yerleşik bağlıdır.

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

Aşağıdaki örnek, mümkün olduğunda yeni API'lerini kullanabilmek için farklı bir hedef çerçeveyi test etme gösterir:

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

[C# başvurusu](../../../csharp/language-reference/index.md)  
[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[C# Ön İşlemci Yönergeleri](index.md)  
[Nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).
