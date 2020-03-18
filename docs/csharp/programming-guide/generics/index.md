---
title: Jenerikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167499"
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)

Jenerikler, bir veya daha fazla türünün belirtimini, sınıf veya yöntem istemci kodu tarafından bildirilene ve anında yapılana kadar erteleyen sınıflar ve yöntemler tasarlamayı mümkün kılmaktadır. Örneğin, genel bir tür parametresi `T`kullanarak, burada gösterildiği gibi, diğer istemci kodunun çalışma zamanı dökümleri veya kutulama işlemleri maliyetini veya riskine maruz kalmadan kullanabileceği tek bir sınıf yazabilirsiniz:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Genel sınıflar ve yöntemler yeniden kullanılabilirliği, tür güvenliğini ve verimliliği, genel olmayan karşılıklarının yapamayacağı şekilde birleştirir. Jenerikler en sık koleksiyonlar ve bunlar üzerinde çalışan yöntemlerle kullanılır. Ad <xref:System.Collections.Generic> alanı birkaç genel tabanlı koleksiyon sınıfları içerir. Genel olmayan koleksiyonlar, örneğin <xref:System.Collections.ArrayList> önerilmez ve uyumluluk amacıyla korunur. Daha fazla bilgi için [.NET'teki Jenerik'e](../../../standard/generics/index.md)bakın.

Tabii ki, aynı zamanda kendi genelleştirilmiş çözümler ve tür güvenli ve verimli tasarım desenleri sağlamak için özel genel türleri ve yöntemleri oluşturabilirsiniz. Aşağıdaki kod örneği, gösteri amacıyla basit bir genel bağlantılı liste sınıfını gösterir. (Çoğu durumda, kendi kitabınızı oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan <xref:System.Collections.Generic.List%601> sınıfı kullanmanız gerekir.) Tür parametresi, `T` listede depolanan maddenin türünü belirtmek için normalde somut bir türün kullanılacağı çeşitli konumlarda kullanılır. Aşağıdaki şekillerde kullanılır:

- `AddHead` Yöntemde yöntem parametresi türü olarak.
- İç içe sınıftaki `Data` `Node` özelliğin dönüş türü olarak.
- İç içe sınıftaki `data` özel üyenin türü olarak.

 İç `T` içe sınıf `Node` için kullanılabilir olduğunu unutmayın. Bir `GenericList<T>` beton türü ile instantiated olduğunda, `GenericList<int>`örneğin bir `T` , her `int`olay ile değiştirilecektir .

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

Aşağıdaki kod örneği, istemci kodunun `GenericList<T>` tamsayılar listesi oluşturmak için genel sınıfı nasıl kullandığını gösterir. Yalnızca tür bağımsız değişkenini değiştirerek, aşağıdaki kod dizeleri veya başka bir özel tür listeleri oluşturmak için kolayca değiştirilebilir:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Genel genel bakış

- Kodun yeniden kullanımını, tür güvenliğini ve performansı en üst düzeye çıkarmak için genel türleri kullanın.
- Generics en yaygın kullanımı toplama sınıfları oluşturmaktır.
- .NET Framework sınıf kitaplığı <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir. Bunlar, ad alanı gibi <xref:System.Collections.ArrayList> sınıflar yerine mümkün olduğunda kullanılmalıdır. <xref:System.Collections>
- Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, etkinliklerinizi ve temsilcilerinizi oluşturabilirsiniz.
- Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.
- Genel bir veri türünde kullanılan türler hakkındaki bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.

## <a name="related-sections"></a>İlgili bölümler

- [Genel Tür Parametreleri](generic-type-parameters.md)
- [Tür Parametrelerindeki Kısıtlamalar](constraints-on-type-parameters.md)
- [Genel Sınıflar](generic-classes.md)
- [Genel Arabirimler](generic-interfaces.md)
- [Genel Yöntemler](generic-methods.md)
- [Genel Temsilciler](generic-delegates.md)
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](differences-between-cpp-templates-and-csharp-generics.md)
- [Genel Türler ve Yansıma](generics-and-reflection.md)
- [Çalışma Zamanındaki Genel Türler](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Türler](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
