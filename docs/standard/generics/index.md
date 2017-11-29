---
title: ".NET Framework'te Genel Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 510d7f30853496409caccab69e68f55a6638319e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="generics-in-the-net-framework"></a>.NET Framework'te Genel Türler
<a name="top"></a>Genel türler yöntemi, sınıf, yapı veya arabirimi temel aldığı kesin veri türüne uyarlamak olanak tanır. Örneğin kullanmak yerine <xref:System.Collections.Hashtable> sınıf sağlayan anahtarlarını ve değerlerini herhangi bir türde olması için kullanabilirsiniz <xref:System.Collections.Generic.Dictionary%602> genel sınıf ve anahtar için izin verilen türü ve izin verilen değer türü belirtin. Genel türlerin yararları arasında artan kod yeniden kullanılırlığı ve tür güvenliği ' dir.  
  
 Bu konu, .NET Framework'teki genel türler genel bir bakış ve genel türleri veya yöntemleri özetini sağlar. Aşağıdaki bölümleri içerir:  
  
-   [Tanımlama ve genel türler kullanma](#defining_and_using_generics)  
  
-   [Genel türler terminolojisi](#generics_terminology)  
  
-   [Sınıf kitaplığı ve dil desteği](#class_library_and_language_support)  
  
-   [İç içe geçmiş türler ve genel türler](#nested_types_and_generics)  
  
-   [İlgili Konular](#related_topics)  
  
-   [Başvuru](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Tanımlama ve genel türler kullanma  
 Genel türler sınıflar, yapılar, arabirimleri ve bir veya daha fazla depolama veya kullanan türü için yer tutucuları (tür parametreleri) sahip yöntemleri durumdadır. Genel koleksiyon sınıfı bir tür parametresi depoladığı nesne türü için bir yer tutucu olarak kullanabilirsiniz; Tür parametreleri, alan türlerini ve yöntemlerinden parametre türleri görünür. Genel yöntem, tür parametresi dönüş değerinin türü veya resmi parametrelerinden birinin türü olarak kullanabilirsiniz. Aşağıdaki kod basit genel sınıf tanımını gösterir.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Genel bir sınıf örneği oluşturduğunuzda, tür parametreleri için yerine gerçek türlerini belirtin. Bu, seçilen türlerinizi tür parametreleri görünen her yerde yerine başvurulan oluşturulan genel bir sınıf, yeni genel bir sınıf oluşturur. Aşağıdaki kodda gösterildiği gibi türleri, tercih ettiğiniz için tasarlanmış bir tür kullanımı uyumlu sınıf sonucudur.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Genel türler terminolojisi  
 Aşağıdaki terimler, .NET Framework'teki genel türler tartışmak için kullanılır:  
  
-   A *genel tür tanımında* bir sınıf, yapı ya da bir şablonla kullanan içeren veya türleri yer tutucular olarak işlev arabirimi bildirimi. Örneğin, <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> sınıfı, iki tür içerebilir: anahtarları ve değerleri. Genel tür tanımında yalnızca bir şablon olduğundan, sınıf, yapı veya genel tür tanımı arabirimi örneği oluşturulamıyor.  
  
-   *Genel tür parametreleri*, veya *tür parametrelerindeki*, yer tutucular genel türü veya yöntemi tanımında şunlardır. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Genel türünde iki tür parametreleri `TKey` ve `TValue`, anahtarları ve değerleri türlerini temsil eder.  
  
-   A *genel tür oluşturulan*, veya *oluşturulan türü*, genel tür tanımında genel tür parametreleri için türlerini belirtme sonucudur.  
  
-   A *genel tür bağımsız değişkeni* için genel tür parametresi yerine herhangi bir tür.  
  
-   Genel bir terim *genel tür* oluşturulan türler ve genel tür tanımlarını içerir.  
  
-   *Kovaryans* ve *değişken karşıtı* genel tür parametreleri, tür bağımsız değişkenleri olan daha türetilmiş (kovaryans) veya daha az türetilmiş (değişken karşıtı) oluşturulan genel türler kullanmanızı oluşturulan bir hedef etkinleştirmek yazın. Kovaryans ve kontravaryans topluca denir *farkı*. Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Kısıtlamaları* sınırları genel tür parametreleri yerleştirilir. Örneğin, uygulama türleri için bir tür parametresi sınırlayabilir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> türdeki örneklerin sıralanabilir emin olmak için genel arabirimi. Tür parametreleri, bir varsayılan oluşturucusu olmalı veya başvuru türleri veya değer türleri olan belirli bir temel sınıf türleri için de kısıtlayabilirsiniz. Genel tür kullanıcılarının kısıtlamalarını karşılamadığı tür bağımsız değişkenleri yerine geçemez.  
  
-   A *genel yöntem tanımını* iki parametre listeleri ile bir yöntemdir: genel tür parametreleri resmi parametrelerin bir listesi ve bir listesi. Tür parametreleri, dönüş türü veya aşağıdaki kodu gösterildiği gibi resmi parametre türleri olarak yer alabilir.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Genel yöntemler genel veya nongeneric türlerinde görünebilir. Bir yöntem yalnızca genel bir tür için ait olduğu veya hatta biçimsel parametrelerine sahip olduğundan, kendilerini kapsayan türle genel parametreleri türleridir genel olmadığından olduğunu dikkate almak önemlidir. Yalnızca kendi türü parametrelerin listesi varsa genel yöntemidir. Aşağıdaki kodda, yalnızca yöntemi `G` geneldir.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Başa dön](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Olumlu ve olumsuz yönleri genel türler  
 Genel koleksiyonlar ve temsilciler kullanarak birçok avantaj vardır:  
  
-   Tür güvenliği. Genel türler tür güvenliği yük sizden derleyiciye shift. Derleme zamanında zorlandığından doğru veri türü için test etmek için kod yazmaya gerek yoktur. Tür atama gereksinimini ve çalışma zamanı hataları olasılığını azaltılır.  
  
-   Daha az kod yazıp kodu daha kolay yeniden. Taban türünden devralan ve üyeleri geçersiz kılma gerek yoktur. Örneğin, <xref:System.Collections.Generic.LinkedList%601> hemen kullanıma hazırdır. Örneğin, aşağıdaki değişken bildirimi ile bağlantılı dizelerinin listesini oluşturabilirsiniz:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Daha iyi performans. Genel koleksiyon türleri genellikle daha iyi depolamak ve değer türleri kutusunda gerek yoktur çünkü değer türleri düzenleme için gerçekleştirin.  
  
-   Genel temsilciler tür kullanımı uyumlu geri aramalar birden çok temsilci sınıfları oluşturmak zorunda kalmadan etkinleştirin. Örneğin, <xref:System.Predicate%601> Genel temsilci sağlar, belirli bir tür için kendi arama ölçütü uygulayan bir yöntem oluşturma ve yönteminizi yöntemleri ile kullanmak için <xref:System.Array> gibi yazın <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, ve <xref:System.Array.FindAll%2A> .  
  
-   Genel türler dinamik olarak üretilen kod kolaylaştırın. Genel türler ile dinamik olarak üretilen kod kullandığınızda türü oluşturmak gerekmez. Bu, tüm derlemeleri oluşturmak yerine basit dinamik yöntemler kullanmak senaryolar sayısını artırır. Daha fazla bilgi için bkz: nasıl yapılır: tanımlayın ve dinamik yöntemleri yürütme ve DynamicMethod.  
  
 Genel türler bazı kısıtlamalar şunlardır:  
  
-   Genel türler türetilmiş çoğu temel sınıflardan gibi <xref:System.MarshalByRefObject> (ve kısıtlamalar, genel tür parametreleri gibi temel sınıfından türetilen gerektirecek şekilde kullanılabilir <xref:System.MarshalByRefObject>). Ancak, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bağlamı bağlı Genel türleri desteklemez. Genel bir tür öğesinden türetilen <xref:System.ContextBoundObject>, ancak neden yazın, örneği oluşturulmaya çalışılırken bir <xref:System.TypeLoadException>.  
  
-   Numaralandırmalar genel tür parametreleri olamaz. (Örneğin, bu Visual Basic, C# veya C++ kullanılarak tanımlanan genel bir tür iç içe yerleştirilmiş çünkü) numaralandırma yalnızca arada genel olabilir. Daha fazla bilgi için bkz: "Numaralandırmalar" [ortak tür sistemi](../../../docs/standard/base-types/common-type-system.md).  
  
-   Basit dinamik yöntemler genel olamaz.  
  
-   Tüm kapsayan türleri tür parametrelerini türleri atanmış sürece Visual Basic, C# ve C++, genel bir tür içine bir iç içe geçmiş tür başlatılamaz. Bu bildiren başka bir yansıma, bu diller kullanılarak tanımlanan bir iç içe geçmiş tür tüm kapsayan türlerinin tür parametreleri içeren yoludur. Bu bir iç içe geçmiş tür üye tanımlarında kullanılacak türleri kapsayan tür parametre sağlar. Daha fazla bilgi için bkz: "Türleri iç içe geçmiş" <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Dinamik bir bütünleştirilmiş kod yayma veya kullanılarak tanımlanmış bir iç içe geçmiş tür [Ilasm.exe (IL derleyici)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) kapsayan türlerinden; tür parametrelerini dahil etmek için gerekli değildir ancak bunları tür parametreleri içermez varsa iç içe geçmiş sınıf kapsamda değildir.  
  
     Daha fazla bilgi için bkz: "Türleri iç içe geçmiş" <xref:System.Type.MakeGenericType%2A>.  
  
 [Başa dön](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Sınıf kitaplığı ve dil desteği  
 .NET Framework şu ad alanlarından genel koleksiyon sınıfları birkaç sağlar:  
  
-   <xref:System.Collections.Generic> Ad alanı .NET Framework tarafından sağlanan gibi genel koleksiyon türleri çoğunu kataloglar <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602> Genel sınıflar.  
  
-   <xref:System.Collections.ObjectModel> Ad alanı kataloglar ek genel koleksiyon türleri gibi <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> nesne modelleri, sınıfların kullanıcılara sunulması için kullanışlı olan genel bir sınıf.  
  
 Sıralama ve eşitlik karşılaştırmaları uygulamak için genel arabirimler içinde verilmiştir <xref:System> olay işleyicileri, dönüştürme ve arama koşulları için genel temsilci türleri ile birlikte ad alanı.  
  
 Genel türler için destek eklenmiştir <xref:System.Reflection> genel türler ve genel yöntemler için incelemek için ad alanı <xref:System.Reflection.Emit> genel türleri ve yöntemleri içeren dinamik derlemeleri Yayma ve için <xref:System.CodeDom> kaynak grafikleri oluşturma genel türler içeren.  
  
 Ortak dil çalışma zamanı yeni işlem kodları ve genel türleri dahil olmak üzere Microsoft Ara dilde (MSIL) desteklemek için önekler sağlar <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, ve <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# ve Visual Basic tüm tanımlama ve genel türler kullanmak için tam destek sağlar. Dil desteği hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [genel türlere giriş](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), ve [genel türler genel bakış Visual C++'ta](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Başa dön](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>İç içe geçmiş türler ve genel türler  
 Genel tür içinde iç içe bir türü kapsayan genel tür türü parametrelere bağlı olabilir. Ortak dil çalışma zamanı genel tür parametreleri kendi yoksa bile genel, olacak şekilde iç içe geçmiş türler göz önünde bulundurur. İç içe geçmiş türünün bir örneği oluşturduğunuzda, tüm kapsayan genel türler için tür bağımsız değişkenleri belirtmeniz gerekir.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET Framework'teki genel koleksiyonlar](../../../docs/standard/generics/collections.md)|Genel koleksiyon sınıfları ve .NET Framework'teki diğer genel türleri açıklanmaktadır.|  
|[Dizi ve listeleri düzenlemek için genel temsilciler](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Bir dizi veya koleksiyon öğeleri üzerinde gerçekleştirilecek genel temsilciler dönüşümleri, arama koşulları ve eylemleri açıklar.|  
|[Genel arabirimler](../../../docs/standard/generics/interfaces.md)|Genel türler aileleri arasında ortak işlevsellik sağlayan genel arabirimler açıklanmaktadır.|  
|[Kovaryans ve kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)|Kovaryans ve kontravaryans genel tür parametreleri açıklar.|  
|[Çok kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md)|.NET Framework'teki genel türleri dahil olmak üzere, koleksiyon türleri kullanım senaryoları ve özellikleri hakkındaki özet bilgileri sağlar.|  
|[Genel koleksiyonları ne zaman kullanılacağı](../../../docs/standard/collections/when-to-use-generic-collections.md)|Ne zaman genel koleksiyon türleri kullanılacağını belirlemek için genel kurallar açıklanmaktadır.|  
|[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Genel türler ve yöntemleri dahil dinamik derlemeleri oluşturma açıklanmaktadır.|  
|[Visual Basic'de genel türler](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Visual Basic kullanıcıları, kullanma ve genel türleri tanımlama için nasıl yapılır konuları dahil olmak üzere genel türler özelliğini açıklar.|  
|[Genel türlere giriş](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Tanımlama ve C# kullanıcılar için genel türler kullanma genel bir bakış sağlar.|  
|[Visual C++'de genel türlere genel bakış](/cpp/windows/overview-of-generics-in-visual-cpp)|Genel türler ve temsilciler arasındaki farklar dahil olmak üzere, C++ kullanıcılar için genel türler özelliğini açıklar.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Başa dön](#top)
