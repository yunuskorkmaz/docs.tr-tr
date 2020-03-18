---
title: .NET içindeki Genel Türler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generic methods, type inference
- generics [.NET Framework], collections
- generic interfaces [.NET Framework]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET Framework]
- generics [.NET Framework], interfaces
- generics [.NET Framework], about
- generics [.NET Framework]
- generic collections [.NET Framework]
- generic delegates [.NET Framework]
- generic type arguments
- generics [.NET Framework], delegates
- generics [.NET Framework], features
- constraints [.NET Framework]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
ms.openlocfilehash: 7f20e5108ad8bff602f5b761e65f093d987f2608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156315"
---
# <a name="generics-in-net"></a>.NET içindeki Genel Türler

Genel ler, bir yöntemi, sınıfı, yapıyı veya arabirimi, üzerinde hareket eden kesin veri türüne uyarlamanızı sağlar. Örneğin, anahtarların <xref:System.Collections.Hashtable> ve değerlerin herhangi bir türde olmasını sağlayan sınıfı kullanmak <xref:System.Collections.Generic.Dictionary%602> yerine, genel sınıfı kullanabilir ve anahtar için izin verilen türü ve değer için izin verilen türü belirtebilirsiniz. Jenerik faydaları arasında artan kod yeniden kullanılabilirliği ve tür güvenliği vardır.  

## <a name="defining-and-using-generics"></a>Genel Leri Tanımlama ve Kullanma
 Genel ler, depoladıkları veya kullandıkları türlerden biri veya daha fazlası için yer tutucuları (tür parametreleri) olan sınıflar, yapılar, arabirimler ve yöntemlerdir. Genel bir koleksiyon sınıfı, depoladığınız nesnelerin türü için yer tutucu olarak bir tür parametresi kullanabilir; tür parametreleri, alanlarının türleri ve yöntemlerinin parametre türleri olarak görünür. Genel bir yöntem, tür parametresini iade değerinin türü olarak veya biçimsel parametrelerinden birinin türü olarak kullanabilir. Aşağıdaki kod basit bir genel sınıf tanımını göstermektedir.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Genel bir sınıfın bir örneğini oluşturduğunuzda, tür parametrelerinin yerine geçecek gerçek türleri belirtirsiniz. Bu, seçilen türleri tür parametrelerinin göründüğü her yerde değiştirilmiştir, oluşturulmuş genel sınıf olarak adlandırılan yeni bir genel sınıf kurar. Sonuç, aşağıdaki kodun gösterdiği gibi, seçtiğiniz türlere göre uyarlanmış tür güvenli bir sınıftır.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Jenerik terminolojisi  
 .NET'teki jenerikleri tartışmak için aşağıdaki terimler kullanılır:  
  
- *Genel tür tanımı,* şablon olarak işlev görebilen ve içerebileceği veya kullanabileceği türler için yer tutucularla birlikte çalışan bir sınıf, yapı veya arabirim bildirimidir. Örneğin, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> sınıf iki tür içerebilir: anahtarlar ve değerler. Genel tür tanımı yalnızca bir şablon olduğundan, genel bir tür tanımı olan bir sınıf, yapı veya arabirim örnekleri oluşturamazsınız.  
  
- *Genel tür parametreleri*veya *tür parametreleri,* genel bir tür veya yöntem tanımında yer tutucularıdır. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Genel tür, anahtarları `TKey` ve `TValue`değerleri türlerini temsil eden iki tür parametreye sahiptir.  
  
- *Yapılandırılan genel tür türü*veya *oluşturulmuş tür,* genel bir tür tanımının genel tür parametreleri için türlerin belirtilmesinin sonucudur.  
  
- *Genel tür bağımsız değişkeni,* genel bir tür parametresi yerine geçen herhangi bir türdür.  
  
- Genel terim *genel türü* hem oluşturulmuş türleri hem de genel tür tanımlarını içerir.  
  
- Genel tür parametrelerinin *tutarlılığı* ve *kontravaryansı,* tür bağımsız değişkenleri hedef oluşturulmuş türe göre daha fazla türetilmiş (covariance) veya daha az türetilmiş (kontrayantüre) olan yapılı genel türleri kullanmanıza olanak tanır. Covariance ve kontravaryans topluca *varyans*olarak adlandırılır. Daha fazla bilgi için Bkz. [Covariance ve Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Kısıtlamalar,* genel tür parametrelerine yerleştirilen sınırlardır. Örneğin, tür örneklerinin sıralanabileceğinden emin <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> olmak için, bir tür parametresini genel arabirimi uygulayan türlerle sınırlayabilirsiniz. Ayrıca, tür parametrelerini belirli bir taban sınıfa sahip, parametresiz bir oluşturucusu olan veya başvuru türleri veya değer türleri olan türlerle sınırlandırabilirsiniz. Genel türdeki kullanıcılar, kısıtlamaları karşılamayan tür bağımsız değişkenlerinin yerini alamaz.  
  
- *Genel yöntem tanımı,* iki parametre listesi içeren bir yöntemdir: genel tür parametrelerinin listesi ve resmi parametrelerin listesi. Tür parametreleri, aşağıdaki kodun gösterdiği gibi, iade türü olarak veya resmi parametrelerin türleri olarak görünebilir.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Genel yöntemler genel veya genel olmayan türlerde görünebilir. Bir yöntemin yalnızca genel bir türe ait olduğu için veya türleri çevreleyen türün genel parametreleri olan resmi parametrelere sahip olduğu için genel olmadığını unutmayın. Bir yöntem yalnızca kendi tür parametreleri listesi varsa geneldir. Aşağıdaki kodda, yalnızca `G` yöntem geneldir.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Jeneriklerin avantajları ve dezavantajları
 Genel koleksiyonları ve temsilcileri kullanmanın birçok avantajı vardır:  
  
- Tür güvenliği. Genel ler tür güvenliği yükünü sizden derleyiciye kaydırın. Derleme zamanında uygulandığından, doğru veri türünü sınamak için kod yazmaya gerek yoktur. Tip döküm ihtiyacı ve çalışma zamanı hataları olasılığı azalır.  
  
- Daha az kod ve kod daha kolay yeniden kullanılır. Bir temel türden devralmaya ve üyeleri geçersiz kılmaya gerek yoktur. Örneğin, hemen <xref:System.Collections.Generic.LinkedList%601> kullanıma hazırdır. Örneğin, aşağıdaki değişken bildirimi ile dizeleri bağlantılı bir liste oluşturabilirsiniz:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Daha iyi performans. Genel koleksiyon türleri genellikle değer türlerini depolamak ve işlemek için daha iyi performans gösterir, çünkü değer türlerini kutuya almaya gerek yoktur.  
  
- Genel temsilciler, birden çok temsilci sınıfı oluşturmaya gerek kalmadan tür güvenli geri aramaları etkinleştirin. Örneğin, <xref:System.Predicate%601> genel temsilci, belirli bir tür için kendi arama ölçütlerinizi uygulayan bir yöntem oluşturmanıza <xref:System.Array> ve <xref:System.Array.Find%2A>yönteminizi , , <xref:System.Array.FindLast%2A>ve <xref:System.Array.FindAll%2A>.  
  
- Genel ler dinamik olarak oluşturulan kodu kolaylaştırır. Dinamik olarak oluşturulmuş koda sahip jenerik kullandığınızda, tür oluşturmanız gerekmez. Bu, tüm derlemeleri oluşturmak yerine hafif dinamik yöntemler kullanabileceğiniz senaryo ların sayısını artırır. Daha fazla bilgi için [bkz: Dinamik Yöntemleri Tanımla ve Yürütün](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) ve. <xref:System.Reflection.Emit.DynamicMethod>  
  
 Aşağıdaki jenerik bazı sınırlamalar şunlardır:  
  
- Genel türler, <xref:System.MarshalByRefObject> (ve kısıtlamalar gibi <xref:System.MarshalByRefObject>temel sınıfların çoğundan türetilebilir). Ancak,.NET Framework bağlama bağlı genel türleri desteklemez. Genel bir tür <xref:System.ContextBoundObject>türetilebilir, ancak bu tür bir <xref:System.TypeLoadException>örnek oluşturmaya çalışırken bir .  
  
- Tümumerations genel tür parametreleri olamaz. Numaralandırma yalnızca genel olabilir (örneğin, Visual Basic, C#veya C++kullanılarak tanımlanan genel bir türde iç içe olduğundan). Daha fazla bilgi için Ortak Tür [Sistemi'ndeki](../../../docs/standard/base-types/common-type-system.md)"Sayısallaştırmalar" adlı kullanıcıya bakın.  
  
- Hafif dinamik yöntemler genel olamaz.  
  
- Visual Basic, C#ve C++'da, genel bir türe dahil edilmiş iç içe bir tür, tüm çevreleyen türlerin tür parametrelerine tür parametreleri atanmadığı sürece anında kullanılamaz. Bunu söylemenin başka bir yolu, yansımada, bu diller kullanılarak tanımlanan iç içe bir tür, tüm çevreleyen türlerinin tür parametrelerini içiçe olmasıdır. Bu, iç içe geçen bir türün üye tanımlarında çevre türlerinin tür parametrelerinin kullanılmasına olanak tanır. Daha fazla bilgi için <xref:System.Type.MakeGenericType%2A>bkz: "İç Içe Türler" içinde.  
  
    > [!NOTE]
    > Dinamik bir derlemede kod yayan veya [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) kullanılarak tanımlanan iç içe bir tür, kendi çevreleyen türlerinin tür parametrelerini eklemek için gerekli değildir; ancak, bunları içermiyorsa, tür parametreleri iç içe sınıf kapsamı içinde değildir.  
  
     Daha fazla bilgi için <xref:System.Type.MakeGenericType%2A>bkz: "İç Içe Türler" içinde.  

## <a name="class-library-and-language-support"></a>Sınıf Kütüphane ve Dil Desteği  
 .NET, aşağıdaki ad alanlarında bir dizi genel toplama sınıfı sağlar:  
  
- Ad <xref:System.Collections.Generic> alanı, .NET tarafından sağlanan genel toplama türlerinin <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602> çoğunu içerir( örneğin, genel sınıflar).  
  
- <xref:System.Collections.ObjectModel> Ad alanı, nesne modellerini sınıflarınızın <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kullanıcılarına teşhir etmek için yararlı olan genel sınıf gibi ek genel koleksiyon türleri içerir.  
  
 Sıralama ve eşitlik karşılaştırmaları uygulamak için genel <xref:System> arabirimler, olay işleyicileri, dönüşümler ve arama yüklemleri için genel temsilci türleri ile birlikte ad alanında sağlanır.  
  
 Genel türleri ve genel yöntemleri <xref:System.Reflection> incelemek, <xref:System.Reflection.Emit> genel türleri ve yöntemleri içeren dinamik derlemeler yayan ve jenerik içeren <xref:System.CodeDom> kaynak grafikler imal etmek için ad alanına genel destek eklendi.  
  
 Ortak dil çalışma süresi, Microsoft ara dilinde (MSIL) genel türleri desteklemek için <xref:System.Reflection.Emit.OpCodes.Stelem> <xref:System.Reflection.Emit.OpCodes.Ldelem>yeni <xref:System.Reflection.Emit.OpCodes.Unbox_Any> <xref:System.Reflection.Emit.OpCodes.Constrained>opcodes <xref:System.Reflection.Emit.OpCodes.Readonly>ve önekler sağlar, dahil olmak üzere , , , ve .  
  
 Visual C++, C#ve Visual Basic tüm genel tanımlar ve kullanmak için tam destek sağlar. Dil desteği hakkında daha fazla bilgi için Visual [Basic'teki Genel Türler](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), [Genel Bilgilere Giriş](../../csharp/programming-guide/generics/index.md)ve Visual [C++'daki Genel Genel Bakış'a](/cpp/windows/overview-of-generics-in-visual-cpp)bakın.

## <a name="nested-types-and-generics"></a>İç Içe Türleri ve Jenerikler  
 Genel bir türde iç içe olan bir tür, çevreleyen genel türün tür parametrelerine bağlı olabilir. Ortak dil çalışma zamanı, kendi genel tür parametreleri olmasa bile iç içe kullanılan türleri genel olarak kabul eder. İç içe bir tür örneği oluşturduğunuzda, tüm genel türleri çevreleyen tür bağımsız değişkenleri belirtmeniz gerekir.  

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET’te Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)|.NET'teki genel koleksiyon sınıflarını ve diğer genel türleri açıklar.|  
|[Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Dönüşümler, arama yüklemleri ve bir dizi veya koleksiyon öğeleri üzerinde yapılacak eylemler için genel temsilcileri açıklar.|  
|[Genel Arabirimler](../../../docs/standard/generics/interfaces.md)|Genel türlerin aileleri arasında ortak işlevsellik sağlayan genel arabirimleri açıklar.|  
|[Covariance ve Kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)|Genel tür parametrelerinde tutarlılık ve kontravaryans açıklar.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|Genel türleri de dahil olmak üzere .NET'teki koleksiyon türlerinin özellikleri ve kullanım senaryoları hakkında özet bilgiler sağlar.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türlerinin ne zaman kullanılacağını belirlemek için genel kuralları açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Genel türleri ve yöntemleri içeren dinamik derlemelerin nasıl oluşturacağı açıklanmaktadır.|  
|[Visual Basic'te Genel Türler](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|Genel türleri kullanmak ve tanımlamak için nasıl yapılan konular da dahil olmak üzere Visual Basic kullanıcılarının genel özelliklerini açıklar.|  
|[Genel Türlere Giriş](../../csharp/programming-guide/generics/index.md)|C# kullanıcıları için genel türleri tanımlama ya da kullanmaya genel bir bakış sağlar.|  
|[Visual C++'de Genel Türlere Genel Bakış](/cpp/windows/overview-of-generics-in-visual-cpp)|Genel bilgiler ve şablonlar arasındaki farklar da dahil olmak üzere C++ kullanıcıları nın jenerik özelliğini açıklar.|  

## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
