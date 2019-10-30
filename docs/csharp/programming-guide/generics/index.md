---
title: Genel türler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 4ff0dd872e1b09e993c947f008c964ad204ad09a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039351"
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)

Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamak için .NET Framework parametre türü kavramını ortaya çıkarabilir. Örneğin, bir genel tür parametresi kullanarak `T`, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini ya da riskini göstermeden, burada gösterildiği gibi, kullanabileceği tek bir sınıf yazabilirsiniz:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Genel sınıflar ve Yöntemler, yeniden kullanılabilirlik, tür güvenliği ve verimliliği genel olmayan karşılıklarının bir şekilde birleştirir. Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır. <xref:System.Collections.Generic> ad alanı, genel tabanlı birkaç koleksiyon sınıfı içerir. <xref:System.Collections.ArrayList> gibi genel olmayan koleksiyonlar önerilmez ve uyumluluk amacıyla korunur. Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).

Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz. Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir. (Çoğu durumda, kendinizinkini oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sunulan <xref:System.Collections.Generic.List%601> sınıfını kullanmanız gerekir.) Tür parametresi `T`, somut bir türün genellikle listede depolanan öğenin türünü belirtmek için kullanıldığı çeşitli konumlarda kullanılır. Aşağıdaki yollarla kullanılır:

- `AddHead` yönteminde bir yöntem parametresinin türü olarak.
- İç içe `Node` sınıfındaki `Data` özelliğinin dönüş türü olarak.
- Özel üyenin türü, iç içe yerleştirilmiş sınıfta `data`.

 `T` iç içe `Node` sınıfı için kullanılabilir olduğunu unutmayın. `GenericList<T>`, `GenericList<int>`gibi somut bir türle başlatıldığında `T` her oluşumu `int`ile yerine geçer.

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)] 

Aşağıdaki kod örneği, istemci kodunun tamsayılar listesini oluşturmak için genel `GenericList<T>` sınıfını nasıl kullandığını gösterir. Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Genel bakışa genel bakış

- Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.
- Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.
- .NET Framework sınıf kitaplığı, <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir. Bunlar, <xref:System.Collections> ad alanındaki <xref:System.Collections.ArrayList> gibi sınıflar yerine mümkün olduğunda kullanılmalıdır.
- Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olaylarınızı ve temsilcilerinizi oluşturabilirsiniz.
- Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.
- Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.

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
- [\<typeparam >](../xmldoc/typeparam.md)
- [\<typeparamref >](../xmldoc/typeparamref.md)
- [.NET 'teki genel türler](../../../standard/generics/index.md)
