---
title: Genel türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423390"
---
# <a name="generics-c-programming-guide"></a>Genel Türler (C# Programlama Kılavuzu)
Genel türler, C# dili ve ortak dil çalışma zamanı (CLR) 2.0 sürümüne eklenmiştir. Genel türler için .NET Framework tasarım sınıfları ve sınıf ya da yöntem bildirildi ve istemci kodu sayesinde örneği kadar bir veya daha fazla tür belirtimi erteleme yöntemlere mümkün hale tür parametrelerinin kavramı tanıtır. Örneğin, bir genel tür parametre T kullanarak diğer istemci kodu çalışma zamanı atamaları veya kutulama işlemleri riskini ve maliyet olmaksızın burada gösterildiği gibi kullanabileceğiniz tek bir sınıf yazabilirsiniz:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

Genel sınıflar ve yöntemler çalışmalarında, tür güvenliği ve verimlilik genel olmayan karşılıkları edilemez bir şekilde birleştirin. Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile sık kullanılır. .NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel tabanlı koleksiyon sınıflarını içerir. Tüm .NET Framework 2.0 ve daha sonra kullanmak yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi hedefleyen uygulamalar, önerilen <xref:System.Collections.ArrayList>. Daha fazla bilgi için [.NET içindeki genel türler](../../../standard/generics/index.md).  
  
 Elbette, özel, genel türler de oluşturabilirsiniz ve kendi sağlamak için yöntemleri çözümleri ve tür açısından güvenli ve verimli tasarım desenleri genelleştirilmiş. Aşağıdaki kod örneği, Tanıtım amaçlı basit bir genel bağlantılı liste sınıfı gösterir. (Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> sınıf kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan.) Tür parametresi `T` çeşitli konumlarda burada somut bir türde normalde kullanılabilir listesinde depolanan öğenin türünü belirtmek için kullanılır. Bu, aşağıdaki şekillerde kullanılır:  
  
- Bir yöntemin parametre türü olarak `AddHead` yöntemi.  
  
- Dönüş türü olarak `Data` iç içe özellik `Node` sınıfı.  
  
- Özel üye türü olarak `data` içinde iç içe geçmiş sınıf.  
  
 T için iç içe geçmiş kullanılabilir olduğunu unutmayın `Node` sınıfı. Zaman `GenericList<T>` somut bir türde örneğin olarak Örneklendirilmiş bir `GenericList<int>`, her geçtiği `T` ile değiştirilecek `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmak için sınıf. Basit tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeler veya başka herhangi bir özel tür listesini oluşturmak için değiştirilmesi:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Genel türlere genel bakış  
  
- Genel türler, kod yeniden kullanımını, tür güvenliği ve performansı en üst düzeye çıkarmak için kullanın.  
  
- Genel türlerin yararları en yaygın kullanımı, koleksiyon sınıfları oluşturmaktır.  
  
- .NET Framework sınıf kitaplığı çeşitli yeni genel koleksiyon sınıflarını içeren <xref:System.Collections.Generic> ad alanı. Olası yerine gibi sınıfların her durumda bu kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.  
  
- Kendi genel arabirimler, sınıflar, yöntemler, olaylar ve temsilciler oluşturabilirsiniz.  
  
- Genel sınıflar, yöntemler belirli veri türlerinde erişimi etkinleştirmek için kısıtlı olabilir.  
  
- Genel veri türü kullanılan türleri hakkında bilgi çalışma zamanında yansıma kullanarak elde edilebilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Genel Tür Parametreleri](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [Tür Parametrelerindeki Kısıtlamalar](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [Genel Arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [Genel Yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [Genel Temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [C++ Şablonları ve C# Genel Türleri Arasındaki Farklar](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Genel Türler ve Yansıma](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [Çalışma Zamanındaki Genel Türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Türler](../../../csharp/programming-guide/types/index.md)
- [\<typeparam >](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref >](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [.NET içindeki genel türler](../../../standard/generics/index.md)
