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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 104a0018896eb95255cf4054f9402ce5160b95f7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584149"
---
# <a name="generics-in-net"></a>.NET içindeki Genel Türler

<a name="top"></a> Genel türler bir yöntemi, sınıf, yapı veya arabirimi temel aldığı hassas veri türüne uyumlu hale getirmenizi sağlar. Örneğin kullanmak yerine <xref:System.Collections.Hashtable> sınıfı, anahtarları ve değerlerini herhangi bir türde olması için veren, kullanabileceğiniz <xref:System.Collections.Generic.Dictionary%602> genel sınıf ve anahtar için izin verilen türü ve değeri için izin verilen türü belirtin. Yararları arasında artan kod çalışmalarında ve tür güvenliği ' dir.  
  
 Bu konu, .NET de genel türlere genel bakış ve genel türleri veya yöntemleri özetini sağlar. Aşağıdaki bölümleri içerir:  
  
-   [Tanımlama ve genel türler kullanma](#defining_and_using_generics)  
  
-   [Genel türler terminolojisi](#generics_terminology)  
  
-   [Sınıf kitaplığı ve dil desteği](#class_library_and_language_support)  
  
-   [İç içe geçmiş türler ve genel türler](#nested_types_and_generics)  
  
-   [İlgili Konular](#related_topics)  
  
-   [Başvuru](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Tanımlama ve genel türler kullanma  
 Genel türler, sınıflar, yapılar, arabirimler ve bir veya daha fazla saklamak veya kullanan türler için yer tutucular (tür parametreleri) sahip yöntemleri ' dir. Genel koleksiyon sınıfı bir tür parametresi, depoladığı nesnelerin türü için yer tutucu olarak kullanabilirsiniz; Tür parametreleri, alan türlerini ve yöntemlerinin parametre türleri görünür. Genel yöntem, tür parametresi, dönüş değerinin türünü ya da bir biçimsel parametrelerinin türünü olarak kullanabilirsiniz. Aşağıdaki kod, basit bir genel sınıf tanımını göstermektedir.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Genel bir sınıf örneğini oluşturduğunuzda, tür parametreleri için yerine gerçek türlerini belirtin. Bu tür parametreleri görünen her yerde yerine, seçilen türleri ile oluşturulmuş bir genel sınıf başvurulan yeni genel bir sınıf oluşturur. Aşağıdaki kodda gösterildiği gibi sonuç türleri, seçiminiz için uygun bir tür kullanımı uyumlu sınıftır.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Genel türler terminolojisi  
 .NET içindeki genel türler tartışmak için aşağıdaki terimler kullanılır:  
  
-   A *genel tür tanımı* sınıfı, yapı veya arabirim bildirimi, bir şablonla, onu içeren depolayabildikleri veya kullanabildikleri türler için yer tutucu işlevini görür. Örneğin, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> sınıfı iki tür içerebilir: anahtarları ve değerleri. Genel tür tanımı yalnızca bir şablon olduğundan, bir sınıf, yapı veya bir genel tür tanımı arabirimi örnekleri oluşturulamaz.  
  
-   *Genel tür parametreleri*, veya *tür parametrelerindeki*, genel bir tür veya yöntem tanımında yer tutuculardır. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Genel türünde iki tür parametreleri `TKey` ve `TValue`, türleri, anahtarları ve değerleri temsil eder.  
  
-   A *oluşturulan genel tür*, veya *oluşturulan türü*, genel tür tanımı genel tür parametrelerinin türlerini belirtme sonucudur.  
  
-   A *genel tür bağımsız değişkeni* bir genel tür parametresi yerine koyulan herhangi bir tür.  
  
-   Genel bir terim *genel tür* oluşturulan türler hem de genel tür tanımlarını içerir.  
  
-   *Kovaryans* ve *kontravaryans* genel tür parametreleri, tür bağımsız değişkenleri: daha fazla türetilmiş (kovaryans) veya daha az türetilmiş (kontravaryans) oluşturulan genel türler kullanmak oluşturulmuş bir hedeften daha etkinleştir yazın. Kovaryans ve kontravaryans topluca denir *varyansı*. Daha fazla bilgi için [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Kısıtlamaları* sınırları, genel tür parametrelerinde yerleştirilir. Örneğin, bir tür parametresine uygulayan türler sınırlayabilir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> türün örneklerinin sıralanabilir emin olmak için genel arabirim. Ayrıca, varsayılan bir oluşturucuya sahip veya başvuru türleri veya değer türleri olan belirli bir temel sınıfa sahip türler için tür parametreleri kısıtlayabilirsiniz. Kullanıcılar genel tür kısıtlamaları karşılamayan tür bağımsız değişkenleri yerine geçemez.  
  
-   A *genel yöntem tanımının* iki parametre listeleri ile bir yöntemdir: genel tür parametreleri ve biçimsel parametrelerinin listesi. Tür parametreleri, dönüş türü veya aşağıdaki kodun gösterdiği olarak biçimsel parametre türleri olarak görünebilir.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Genel yöntemler, genel veya jenerik olmayan türlerde görünebilir. Bir yöntem yalnızca bir genel türe ait ya da bile, biçimsel parametre içerdiğinden eşleşen türleri ve kapsayan türdeki genel parametrelere için genel olmadığına dikkat edin önemlidir. Bir yalnızca kendi tür parametreleri listesi varsa genel yöntemdir. Aşağıdaki kodda, yalnızca yöntemi `G` geneldir.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Başa dön](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Olumlu ve olumsuz yönleri genel türler  
 Genel koleksiyonlar ve temsilciler kullanmanın birçok avantajı vardır:  
  
-   Tür güvenliği. Genel türler tür güvenliği yük, derleyiciye kaydır. Derleme zamanında zorunlu kılındığından için doğru veri türünü test etmek için kod yazmaya gerek yoktur. Tür atama gereksinimini ve çalışma zamanı hataları olasılığı azaltılır.  
  
-   Daha az kod ve kodu daha kolay yeniden. Üyeleri geçersiz kılın ve bir temel tür devralmasına gerek yoktur. Örneğin, <xref:System.Collections.Generic.LinkedList%601> hemen kullanıma hazırdır. Örneğin, aşağıdaki değişken bildirimini ile bağlantılı bir dize listesi oluşturabilirsiniz:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Daha iyi performans. Genel koleksiyon türleri genellikle daha iyi depolamak ve değer türleri kutusunda gerek olmadığından değer türleri düzenleme için gerçekleştirin.  
  
-   Genel temsilciler, tür kullanımı uyumlu geri çağırmaları sınıfları birden çok temsilci oluşturmak zorunda kalmadan etkinleştirin. Örneğin, <xref:System.Predicate%601> Genel temsilci sağlar, belirli bir tür için kendi arama ölçütü uygulayan bir yöntem oluşturmak ve yönteminiz yöntemleri ile kullanmak için <xref:System.Array> gibi yazın <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, ve <xref:System.Array.FindAll%2A> .  
  
-   Genel türler, dinamik olarak üretilen kod kolaylaştırın. Genel türler ile dinamik olarak üretilen kod kullandığınızda tür oluşturma gerekmez. Bu, tüm derlemeler üretmek yerine basit dinamik yöntemler kullanmak senaryoları sayısını artırır. Daha fazla bilgi için [nasıl yapılır: tanımlayın ve dinamik yöntemleri çalıştırma](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) ve <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Bazı sınırlamalar genel türlerin yararları şunlardır:  
  
-   Genel türler türetilmiş çoğu temel sınıftan gibi <xref:System.MarshalByRefObject> (ve sınırlamalar genel tür parametreleri gibi temel sınıflarından türetilen gerektirecek şekilde kullanılabilecek <xref:System.MarshalByRefObject>). Ancak, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bağlam bağlı Genel türleri desteklemez. Genel bir tür türetildiğinde <xref:System.ContextBoundObject>, ancak nedenleri yazın, örneği oluşturulmaya çalışılırken bir <xref:System.TypeLoadException>.  
  
-   Numaralandırmalar, genel tür parametrelerine sahip olamaz. (Örneğin, Visual Basic, C# veya C++ kullanarak tanımlanan genel tür içinde iç içe) bir sabit listesi yalnızca bu arada genel olabilir. Daha fazla bilgi için bkz: "Numaralandırmalar" [ortak tür sistemi](../../../docs/standard/base-types/common-type-system.md).  
  
-   Basit bir dinamik yöntem genel olamaz.  
  
-   Türleri için tür parametreleri tüm kapsayan tür atanmış sürece Visual Basic, C# ve C++ içinde genel tür içinde alınmış iç içe bir tür örneği oluşturulamıyor. Bu belirten başka bir yansıma, bu diller kullanılarak tanımlanır iç içe bir tür tüm kapsayan türlerin tür parametrelerini içerir yoludur. Bu, iç içe türün üye tanımlarında kullanılan türleri kapsayan türü parametre sağlar. Daha fazla bilgi için bkz: "İç içe türler" <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Kullanarak veya dinamik bir derleme, kodu yayan tarafından tanımlanan iç içe bir tür [Ilasm.exe (IL derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) kapsayan türlerinden; tür parametreleri eklemek için gerekli değildir ancak durumunda bunları, tür parametreleri içermez iç içe geçmiş sınıf kapsamında değildir.  
  
     Daha fazla bilgi için bkz: "İç içe türler" <xref:System.Type.MakeGenericType%2A>.  
  
 [Başa dön](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Sınıf kitaplığı ve dil desteği  
 .NET genel koleksiyon sınıflarına aşağıdaki alanlarında sunar:  
  
-   <xref:System.Collections.Generic> Ad alanı içerir gibi .NET tarafından sağlanan genel koleksiyon türlerinin çoğu <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602> Genel sınıflar.  
  
-   <xref:System.Collections.ObjectModel> Ad alanı içeren ek bir genel koleksiyon türleri gibi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nesne modelleri, sınıfları kullanıcılara sunulması için kullanışlı olan genel bir sınıf.  
  
 Genel arabirimler, sıralama ve eşitlik karşılaştırmaları uygulamak için sağlanan <xref:System> olay işleyicileri, dönüştürme ve terimlere arama yüklemleri Genel temsilci türleriyle birlikte ad alanı.  
  
 Genel türler için destek eklendi <xref:System.Reflection> genel türler ve genel metotlar için inceleme için ad alanı <xref:System.Reflection.Emit> genel türleri ve yöntemleri içeren dinamik derlemeler yayan ve için <xref:System.CodeDom> kaynak grafikleri oluşturmak için Bu, genel türler içerir.  
  
 Yeni işlem kodları ve Microsoft Ara dilini (MSIL) dahil olmak üzere genel türleri desteklemek için alan ön eklerini ortak dil çalışma zamanı sağlar <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, ve <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# ve Visual Basic tüm tanımlama ve genel türler kullanmak için tam destek sağlar. Dil desteği hakkında daha fazla bilgi için bkz. [Visual Basic'de genel türler](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [genel türlere giriş](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), ve [genel türlere genel bakış Visual C++'ta](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Başa dön](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>İç içe geçmiş türler ve genel türler  
 Genel tür içinde iç içe geçmiş bir tür kapsayan genel tür türü parametrelere bağlı olabilir. Ortak dil çalışma zamanı, kendi genel tür parametreleri yoksa bile genellenemez için iç içe geçmiş türler göz önünde bulundurur. İç içe türün örneğini oluşturduğunuzda, tüm kapsayan genel türlerin tür bağımsız değişkenleri belirtmeniz gerekir.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET’te Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)|Genel amaçlı koleksiyon sınıfları ve. NET'te diğer genel türler açıklanmaktadır.|  
|[Dizi ve Listeleri Düzenlemek için Genel Temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Bir dizi veya koleksiyon öğeleri üzerinde gerçekleştirilecek genel temsilciler dönüştürmeler, arama koşulları ve eylemleri açıklar.|  
|[Genel Arabirimler](../../../docs/standard/generics/interfaces.md)|Genel türlerin aileleri arasında ortak işlevselliği sağlayan genel arabirimler açıklanmaktadır.|  
|[Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)|Kovaryans ve kontravaryans, genel tür parametreleri açıklar.|  
|[Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|. NET'te genel türleri dahil olmak üzere, koleksiyon türlerinin kullanım senaryoları ve özellikleri hakkındaki özet bilgileri sağlar.|  
|[Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../docs/standard/collections/when-to-use-generic-collections.md)|Genel koleksiyon türleri kullanma zamanı belirlemek için genel kurallar açıklanmaktadır.|  
|[Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Genel türler ve yöntemler içeren dinamik derlemeler oluşturma adımları açıklanmaktadır.|  
|[Visual Basic'de genel türler](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Visual Basic kullanıcıları, genel türleri tanımlama ve kullanma için nasıl yapılır konuları da dahil olmak üzere genel türler özelliğini açıklar.|  
|[Genel Türlere Giriş](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Tanımlama ve C# kullanıcılar için genel türleri kullanarak genel bir bakış sağlar.|  
|[Visual C++'de Genel Türlere Genel Bakış](/cpp/windows/overview-of-generics-in-visual-cpp)|C++ kullanıcı için genel türler ve şablonlar arasındaki farklar dahil olmak üzere genel türler özelliğini açıklar.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Başa dön](#top)
