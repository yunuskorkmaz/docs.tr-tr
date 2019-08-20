---
title: Genel türler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589597"
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)
C# Dil sürüm 2,0 ve ortak dil çalışma zamanı (CLR) için genel türler eklenmiştir. Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamayı sağlayan tür parametrelerinin kavramının .NET Framework sunar. Örneğin, bir genel tür parametresi kullanarak, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini veya riskini aşmadan kullanabileceği tek bir sınıf yazabilirsiniz, burada gösterildiği gibi:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

Genel sınıflar ve Yöntemler, yeniden kullanılabilirliği birleştirir, güvenlik ve verimliliği genel olmayan karşılıklarına göre bir şekilde yazın. Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır. .NET Framework sınıf kitaplığının 2,0 sürümü, birkaç yeni genel tabanlı koleksiyon sınıfı <xref:System.Collections.Generic>içeren yeni bir ad alanı sağlar. .NET Framework 2,0 ve üstünü hedefleyen tüm uygulamaların, gibi eski genel olmayan karşılıkları <xref:System.Collections.ArrayList>yerine yeni genel koleksiyon sınıflarını kullanması önerilir. Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).  
  
 Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz. Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir. (Çoğu durumda, kendi örneğini oluşturmak yerine .NET Framework <xref:System.Collections.Generic.List%601> sınıf kitaplığı tarafından sunulan sınıfı kullanmanız gerekir.) Tür parametresi `T` , somut bir türün listede depolanan öğenin türünü belirtmek için normalde kullanıldığı çeşitli konumlarda kullanılır. Aşağıdaki yollarla kullanılır:  
  
- `AddHead` Yöntem içindeki yöntem parametresinin türü olarak.  
  
- İç içe yerleştirilmiş `Data` `Node` sınıftaki özelliğinin dönüş türü olarak.  
  
- İç içe yerleştirilmiş sınıftaki özel üyenin `data` türü olarak.  
  
 Bu T 'in iç içe yerleştirilmiş `Node` sınıf için kullanılabilir olduğunu unutmayın. , Örneğin, bir `GenericList<int>`somut tür ile örneği oluşturulduğunda, öğesinin `T` her oluşumu ile `int`yerine kullanılır. `GenericList<T>`  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Aşağıdaki kod örneği, istemci kodunun tamsayılar listesini oluşturmak için genel `GenericList<T>` sınıfı nasıl kullandığını gösterir. Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Genel bakışa genel bakış  
  
- Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.  
  
- Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.  
  
- .NET Framework sınıf kitaplığı, <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir. Bunlar, <xref:System.Collections.ArrayList> <xref:System.Collections> ad alanı gibi sınıflar yerine mümkün olduğunda kullanılmalıdır.  
  
- Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olayları ve temsilcilerinizi oluşturabilirsiniz.  
  
- Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.  
  
- Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Genel Tür Parametreleri](./generic-type-parameters.md)  
  
- [Tür Parametrelerindeki Kısıtlamalar](./constraints-on-type-parameters.md)  
  
- [Genel Sınıflar](./generic-classes.md)  
  
- [Genel Arabirimler](./generic-interfaces.md)  
  
- [Genel Yöntemler](./generic-methods.md)  
  
- [Genel Temsilciler](./generic-delegates.md)  
  
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Genel Türler ve Yansıma](./generics-and-reflection.md)  
  
- [Çalışma Zamanındaki Genel Türler](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Türler](../types/index.md)
- [\<typeparam >](../xmldoc/typeparam.md)
- [\<typeparamref >](../xmldoc/typeparamref.md)
- [.NET 'teki genel türler](../../../standard/generics/index.md)
