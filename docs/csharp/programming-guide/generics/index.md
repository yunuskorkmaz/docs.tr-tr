---
title: Genel türler-C# Programlama Kılavuzu
description: Genel türler hakkında bilgi edinin. Genel türler kod yeniden kullanımını, tür güvenliğini ve performansı en üst düzeye çıkarır ve genellikle koleksiyon sınıfları oluşturmak için kullanılır.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: beef9c20e3ac62505bc7a4584b404637935de1dc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299402"
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)

Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamayı sağlayan .NET 'e parametre türü kavramını getirir. Örneğin, genel bir tür parametresi kullanarak `T` , burada gösterildiği gibi, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini veya riskini ortadan kaldırarak kullanabileceği tek bir sınıf yazabilirsiniz:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Genel sınıflar ve Yöntemler, yeniden kullanılabilirlik, tür güvenliği ve verimliliği genel olmayan karşılıklarının bir şekilde birleştirir. Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır. <xref:System.Collections.Generic>Ad alanı, birkaç genel tabanlı koleksiyon sınıfı içerir. Genel olmayan koleksiyonlar, gibi <xref:System.Collections.ArrayList> önerilmez ve uyumluluk amacıyla korunur. Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).

Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz. Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir. (Çoğu durumda, <xref:System.Collections.Generic.List%601> kendinizinkini oluşturmak yerine .NET tarafından sunulan sınıfı kullanmanız gerekir.) Tür parametresi, `T` somut bir türün listede depolanan öğenin türünü belirtmek için normalde kullanıldığı çeşitli konumlarda kullanılır. Aşağıdaki yollarla kullanılır:

- Yöntem içindeki yöntem parametresinin türü olarak `AddHead` .
- `Data`İç içe yerleştirilmiş sınıftaki özelliğinin dönüş türü olarak `Node` .
- `data`İç içe yerleştirilmiş sınıftaki özel üyenin türü olarak.

 `T`İç içe yerleştirilmiş sınıf için kullanılabilir olduğunu unutmayın `Node` . , `GenericList<T>` Örneğin, bir somut tür ile örneği oluşturulduğunda, `GenericList<int>` öğesinin her oluşumu `T` ile yerine kullanılır `int` .

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

Aşağıdaki kod örneği, istemci kodunun `GenericList<T>` tamsayılar listesini oluşturmak için genel sınıfı nasıl kullandığını gösterir. Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Genel bakışa genel bakış

- Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.
- Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.
- .NET sınıf kitaplığı, ad alanındaki çeşitli genel koleksiyon sınıflarını içerir <xref:System.Collections.Generic> . Bunlar <xref:System.Collections.ArrayList> , ad alanı gibi sınıflar yerine mümkün olduğunda kullanılmalıdır <xref:System.Collections> .
- Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olaylarınızı ve temsilcilerinizi oluşturabilirsiniz.
- Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.
- Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.

## <a name="related-sections"></a>İlgili bölümler

- [Genel Tür Parametreleri](generic-type-parameters.md)
- [Tür Parametrelerindeki Kısıtlamalar](constraints-on-type-parameters.md)
- [Genel Sınıflar](generic-classes.md)
- [Genel arabirimler](generic-interfaces.md)
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
