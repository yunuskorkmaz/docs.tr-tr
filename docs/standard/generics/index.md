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
ms.openlocfilehash: f04b6fcd1641a53efe75d38ab7122967bff6a58d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708377"
---
# <a name="generics-in-net"></a>.NET içindeki Genel Türler

Genel türler, bir yöntemi, sınıfı, yapıyı veya arabirimi üzerinde çalıştığı kesin veri türüne göre uyarlamanızı sağlar. Örneğin, anahtarlar ve değerlerin herhangi bir türde olmasına izin veren <xref:System.Collections.Hashtable> sınıfını kullanmak yerine, <xref:System.Collections.Generic.Dictionary%602> genel sınıfını kullanabilir ve anahtar için izin verilen türü ve değer için izin verilen türü belirtebilirsiniz. Genel türlerin avantajları arasında kod yeniden kullanılabilirliği ve tür güvenliği artar.  

## <a name="defining-and-using-generics"></a>Genel türleri tanımlama ve kullanma
 Genel türler, depotıkları veya kullandıkları bir veya daha fazla türden bir veya daha fazla yer tutucu (tür parametreleri) içeren sınıflar, yapılar, arabirimler ve yöntemlerdir. Genel koleksiyon sınıfı, bir tür parametresini, depoladığı nesnelerin türü için yer tutucu olarak kullanabilir; tür parametreleri, alanlarının türleri ve yöntemlerinin parametre türleri olarak görüntülenir. Genel bir yöntem, kendi tür parametresini dönüş değerinin türü veya resmi parametrelerinden birinin türü olarak kullanabilir. Aşağıdaki kod basit bir genel sınıf tanımını gösterir.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Bir genel sınıfın örneğini oluşturduğunuzda, tür parametrelerinin yerine konacak gerçek türleri belirtirsiniz. Bu, seçilen türleriniz tür parametrelerinin göründüğü her yerde yerine, oluşturulmuş bir genel sınıf olarak adlandırılan yeni bir genel sınıf oluşturur. Sonuç olarak, aşağıdaki kodda gösterildiği gibi, türü seçiminiz için uygun olan tür açısından güvenli bir sınıftır.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Genel türler terminolojisi  
 .NET ' te genel türleri tartışmak için aşağıdaki terimler kullanılır:  
  
- *Genel tür tanımı* , şablon olarak işlev gören veya kullanabileceği türlerin yer tutucuları içeren bir sınıf, yapı veya arabirim bildirimidir. Örneğin, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> sınıfı iki tür içerebilir: anahtarlar ve değerler. Genel tür tanımı yalnızca bir şablon olduğundan, bir sınıf, yapı veya genel tür tanımı olan arabirimin örneklerini oluşturamazsınız.  
  
- Genel tür *parametreleri*veya *tür parametreleri*, genel tür veya yöntem tanımında yer tutuculardır. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> genel türü, anahtar ve değer türlerini temsil eden `TKey` ve `TValue`olmak üzere iki tür parametresine sahiptir.  
  
- *Oluşturulmuş bir genel*tür veya *oluşturulmuş tür*, genel tür tanımının genel tür parametreleri için türleri belirtmenin sonucudur.  
  
- *Genel tür bağımsız değişkeni* , genel tür parametresi için değiştirilen herhangi bir türdür.  
  
- Genel terim genel *türü* hem oluşturulmuş türleri hem de genel tür tanımlarını içerir.  
  
- Genel tür parametrelerinin *Kovaryans* ve *değişken varyansı* , tür bağımsız değişkenleri hedef oluşturulmuş bir türden daha fazla türetilmiş (Kovaryans) veya daha az türetilmiş (değişken varyans) olan oluşturulmuş genel türleri kullanmanıza olanak sağlar. Kovaryans ve değişken Varyans, toplu olarak *fark*olarak adlandırılır. Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Kısıtlamalar* , genel tür parametrelerine yerleştirilmiş sınırlardır. Örneğin, tür örneklerinin sıralanabilmesi için, bir tür parametresini <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> genel arabirimini uygulayan türlerle sınırlayabilirsiniz. Ayrıca tür parametrelerini, parametresiz oluşturucusu olan veya başvuru türleri veya değer türleri olan belirli bir temel sınıfı olan türlerle kısıtlayabilirsiniz. Genel tür kullanıcıları, kısıtlamaları karşılamayan tür bağımsız değişkenlerini yerine geçemez.  
  
- *Genel yöntem tanımı* iki parametre listesi olan bir yöntemdir: genel tür parametrelerinin listesi ve bir biçimsel parametre listesi. Tür parametreleri, aşağıdaki kodda gösterildiği gibi, dönüş türü olarak veya biçimsel parametrelerin türleri olarak görünebilir.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Genel metotlar genel veya genel olmayan türlerde bulunabilir. Bir yöntemi genel bir türe ait olduğundan ya da türleri kapsayan türün genel parametreleri olan biçimsel parametrelere sahip olduğundan, bir yöntemin genel olmadığından emin olmak önemlidir. Bir yöntem, yalnızca kendi tür parametreleri listesine sahipse geneldir. Aşağıdaki kodda yalnızca Yöntem `G` geneldir.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Genel türlerin avantajları ve dezavantajları
 Genel koleksiyonları ve temsilcileri kullanmanın birçok avantajı vardır:  
  
- Tür güvenliği. Genel türler, türden güvenlik yükünü derleyicisinden derleyiciye kaydır. Derleme zamanında zorlandığından, doğru veri türü için test etmek için kod yazmanıza gerek yoktur. Tür atama ihtiyacı ve çalışma zamanı hatalarının olma olasılığı azalır.  
  
- Daha az kod ve kod daha kolay yeniden kullanılır. Temel türden devralma ve üyeleri geçersiz kılma gerekmez. Örneğin, <xref:System.Collections.Generic.LinkedList%601> hemen kullanıma yönelik kullanıma yöneliktir. Örneğin, aşağıdaki değişken bildirimiyle bağlantılı dizelerin bir listesini oluşturabilirsiniz:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Daha iyi performans. Genel koleksiyon türleri genellikle değer türlerini saklamak ve işlemek için daha iyi performans sağlar çünkü değer türlerini Box 'a gerek kalmaz.  
  
- Genel Temsilciler, birden çok temsilci sınıfı oluşturmaya gerek kalmadan tür güvenli geri çağırmaları etkinleştirir. Örneğin, <xref:System.Predicate%601> genel temsilci, belirli bir tür için kendi arama ölçütlerinizi uygulayan bir yöntem oluşturmanıza ve yönteminizi <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>ve <xref:System.Array.FindAll%2A>gibi <xref:System.Array> türünün yöntemleriyle kullanmanızı sağlar.  
  
- Dinamik olarak üretilen kodu verimli hale getirin. Dinamik olarak üretilen kodla genel türler kullandığınızda, türü oluşturmanız gerekmez. Bu, tüm derlemeleri oluşturmak yerine, basit dinamik yöntemleri kullanabileceğiniz senaryoların sayısını artırır. Daha fazla bilgi için bkz. [nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) ve <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Genel türlerde bazı sınırlamalar aşağıda verilmiştir:  
  
- Genel türler, <xref:System.MarshalByRefObject> gibi çoğu temel sınıftan türetilebilir (ve kısıtlamalar, genel tür parametrelerinin <xref:System.MarshalByRefObject>gibi temel sınıflardan türemesini gerektirmek için kullanılabilir). Ancak .NET Framework, bağlama dayalı genel türleri desteklemez. Genel bir tür <xref:System.ContextBoundObject>türetilebilir, ancak bu türün bir örneğini oluşturmaya çalışmak <xref:System.TypeLoadException>neden olur.  
  
- Numaralandırmalar genel tür parametrelerine sahip olamaz. Numaralandırma yalnızca genel arada (örneğin, Visual Basic, C#veya C++kullanılarak tanımlanan genel bir tür içinde iç içe yerleştirilmiş olduğundan) olabilir. Daha fazla bilgi için bkz. [ortak tür sisteminde](../../../docs/standard/base-types/common-type-system.md)"numaralandırmalar".  
  
- Hafif dinamik yöntemler genel olamaz.  
  
- Visual Basic, C#ve ' de C++, tüm kapsayan türlerin tür parametrelerine atanmış türler yoksa, ve ' de genel tür içine alınmış iç içe bir tür başlatılamaz. Bu, yansıma içinde, bu diller kullanılarak tanımlanan bir iç içe türün, kapsayan tüm türlerin tür parametrelerini içerir. Bu, kapsayan türlerin tür parametrelerinin iç içe geçmiş bir türün üye tanımlarında kullanılmasına izin verir. Daha fazla bilgi için <xref:System.Type.MakeGenericType%2A>içindeki "Iç Içe türler" başlığına bakın.  
  
    > [!NOTE]
    > Dinamik bir derlemede kod göndererek veya [Ilasm. exe (Il Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) kullanılarak tanımlanan iç içe bir tür, kapsayan türlerin tür parametrelerini içermesi gerekmez; Ancak, bunları içermiyorsa, tür parametreleri iç içe yerleştirilmiş sınıftaki kapsam içinde değildir.  
  
     Daha fazla bilgi için <xref:System.Type.MakeGenericType%2A>içindeki "Iç Içe türler" başlığına bakın.  

## <a name="class-library-and-language-support"></a>Sınıf kitaplığı ve dil desteği  
 .NET aşağıdaki ad alanlarında çok sayıda genel koleksiyon sınıfı sağlar:  
  
- <xref:System.Collections.Generic> ad alanı, .NET tarafından sunulan <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602> genel sınıflar gibi genel koleksiyon türlerinin çoğunu içerir.  
  
- <xref:System.Collections.ObjectModel> ad alanı, sınıflarınızın kullanıcılarına nesne modellerini göstermek için yararlı olan <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> genel sınıf gibi ek genel koleksiyon türleri içerir.  
  
 Sıralama ve eşitlik karşılaştırmaları uygulamak için genel arabirimler, olay işleyicileri, dönüştürmeler ve arama koşullarına ilişkin genel temsilci türleriyle birlikte <xref:System> ad alanında verilmiştir.  
  
 Genel türleri ve genel yöntemleri incelemek için <xref:System.Reflection> ad alanına, genel türler ve Yöntemler içeren dinamik derlemeler ve genel türler içeren kaynak grafikler oluşturmak için <xref:System.CodeDom> <xref:System.Reflection.Emit> için genel türler için destek eklenmiştir.  
  
 Ortak dil çalışma zamanı, Microsoft ara dili (MSIL) içindeki <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>ve <xref:System.Reflection.Emit.OpCodes.Readonly>gibi genel türleri desteklemek için yeni opkodlara ve önekleri sağlar.  
  
 Visual C++, C#ve Visual Basic hepsi, genel türleri tanımlamaya ve kullanmaya yönelik tam destek sağlar. Dil desteği hakkında daha fazla bilgi için bkz. [Visual Basic genel türler](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), Genel türlere [giriş](../../csharp/programming-guide/generics/index.md)ve [Visual C++'teki genel bakışa genel bakış ](/cpp/windows/overview-of-generics-in-visual-cpp). 

## <a name="nested-types-and-generics"></a>İç içe türler ve genel türler  
 Genel türde iç içe yerleştirilmiş bir tür, kapsayan genel türün tür parametrelerine bağlı olabilir. Ortak dil çalışma zamanı, iç içe geçmiş türleri kendi genel tür parametrelerine sahip olmasalar bile genel olacak şekilde değerlendirir. İç içe geçmiş bir türün örneğini oluşturduğunuzda, kapsayan tüm genel türler için tür bağımsız değişkenleri belirtmeniz gerekir.  

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET’te Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)|.NET 'teki genel koleksiyon sınıflarını ve diğer genel türleri açıklar.|  
|[Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Bir dizi veya koleksiyonun öğelerinde yapılacak dönüşümler, arama koşulları ve eylemler için genel temsilcileri açıklar.|  
|[Genel Arabirimler](../../../docs/standard/generics/interfaces.md)|Genel türlerin aileleri arasında ortak işlevsellik sağlayan genel arabirimleri açıklar.|  
|[Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)|Genel tür parametrelerindeki Kovaryans ve değişken varyansı açıklar.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|.NET 'teki genel türler dahil olmak üzere koleksiyon türlerinin özellikleri ve kullanım senaryoları hakkında özet bilgiler sağlar.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türlerinin ne zaman kullanılacağını belirlemek için genel kuralları açıklar.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Genel türleri ve yöntemleri içeren dinamik derlemelerin nasıl oluşturulacağını açıklar.|  
|[Visual Basic genel türler](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|Genel türleri kullanma ve tanımlama hakkında nasıl yapılır konuları dahil olmak üzere Visual Basic kullanıcılarına yönelik genel türler özelliğini açıklar.|  
|[Genel Türlere Giriş](../../csharp/programming-guide/generics/index.md)|Kullanıcılar için C# genel türler tanımlama ve kullanma konusuna genel bakış sunar.|  
|[Visual C++'de Genel Türlere Genel Bakış](/cpp/windows/overview-of-generics-in-visual-cpp)|Genel türler ve şablonlar arasındaki C++ farklılıklar dahil olmak üzere kullanıcılar için genel türler özelliğini açıklar.|  

## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
