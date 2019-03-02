---
title: Nesneleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 5e028ecd6e448237d192894c4a02233c1e0dd4c0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201501"
---
# <a name="objects-c-programming-guide"></a>Nesneler (C# Programlama Kılavuzu)
Bir sınıf veya yapı tanımı türü neler yapabileceğinizi belirten gibi plandır. Bir temel olarak ayrılmış ve şema göre yapılandırılmış bir bellek bloğunu nesnedir. Bir program, aynı sınıfın birçok nesne oluşturabilir. Nesne örneği olarak da adlandırılır ve adlandırılmış bir değişkeni veya bir dizi veya koleksiyon depolanabilir. İstemci kodu yöntemleri çağırın ve nesneyi genel özelliklerine erişmek için bu değişkenleri kullanır koda karşılık gelir. Bir nesne yönelimli dil C# gibi bir programın normal dinamik olarak etkileşim sahip birden çok nesne oluşur.  
  
> [!NOTE]
>  Statik türleri burada açıklanan'den farklı davranır. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Yapı örnekleri vs. Sınıf örnekleri  
 Başvuru türleri sınıflar olduğu için bir sınıf nesnesi bir değişken yönetilen yığında nesnenin adresi için bir başvuru içerir. İkinci bir nesnesinin aynı türdeki ilk nesneye atanırsa, her iki değişken Bu adresteki bir nesneye başvurun. Bu nokta, bu konunun ilerleyen bölümlerinde daha ayrıntılı ele alınmıştır.  
  
 Sınıfların örneklerini kullanılarak oluşturulan [new işleci](../../../csharp/language-reference/keywords/new-operator.md). Aşağıdaki örnekte, `Person` türüdür ve `person1` ve `person 2` örnekleri ya da nesnelerin türü.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Yapılar değer türleri olduğundan, bir değişken bir yapı nesnesinin tüm nesnesinin bir kopyasını tutar. Yapılar örneği de oluşturulabilir kullanarak `new` işleci, ancak bu zorunlu değildir, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Hem bellek `p1` ve `p2` iş parçacığı yığında ayrılır. Bu bellek tür veya yöntem içinde bildirildiği birlikte geri kazanılır. Yapılar atamada neden kopyalanır nedenlerinden biri budur. Nesne tüm başvuruları kapsam dışına sahiplikten aksine, bir sınıf örneği için ayrılan bellek (otomatik olarak geri kazanılan çöp olarak toplanacak) ortak dil çalışma zamanı tarafından andır. C++'ta gibi bir sınıf nesnesi belirleyici yok etmek mümkün değildir. Çöp toplama hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bkz: [çöp toplama](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Ayırmayı ve ayırmayı kaldırma yönetilen yığında bellek ortak dil çalışma zamanı yüksek oranda iyileştirilmiş. Çoğu durumda bir sınıf örneği yığında bir struct örneği ayırma karşı yığınındaki ayırma performans maliyeti, önemli bir fark yoktur.  
  
## <a name="object-identity-vs-value-equality"></a>Nesne Kimliği vs. Değer eşitliği  
 Eşitlik için iki nesneleri karşılaştırmak, iki değişken aynı nesneye bellekte olup olmadığını temsil eder ve bir veya daha fazla alanlarının değerlerini eşdeğer olup bilmek istemediğiniz ilk ayırdetmek. Değerleri Karşılaştır amaçlanıyorsa nesnenin örneğini değer türleri (yapı) veya başvuru türleri (sınıflar, temsilciler, diziler) olup olmadığını dikkate almanız gerekir.  
  
-   İki sınıf örnekleri bellekte aynı konuma başvurmadığını belirlemek için (yani aynı sahip olduğunuzu *kimlik*), statik <xref:System.Object.Equals%2A> yöntemi. (<xref:System.Object?displayProperty=nameWithType> tüm değer türleri ve kullanıcı tarafından tanımlanan yapıları ve sınıfları da dahil olmak üzere, başvuru türleri için örtük temel sınıftır.)  
  
-   İki yapısı örneği örnek alanları aynı değerlere sahip olup olmadığını belirlemek için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi. Tüm yapıları öğesinden örtük olarak devraldığı <xref:System.ValueType?displayProperty=nameWithType>, doğrudan nesne üzerinde aşağıdaki örnekte gösterildiği gibi yöntemi çağırın:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Uygulaması `Equals` yansıma kullanır, çünkü bir yapıda alanlar nelerdir belirlemek mümkün olması gerekir. Kendi yapılar oluştururken, geçersiz kılma `Equals` türünüz için belirli bir verimli eşitlik algoritma sağlamak için yöntemi.  
  
-   İki sınıf örnekleri, alanların değerlerini eşit olup olmadığını belirlemek için kullanmanız mümkün olabilir <xref:System.Object.Equals%2A> yöntemi veya [== işleci](../../../csharp/language-reference/operators/equality-comparison-operator.md). Sınıfı geçersiz veya bunların hangi "eşitlik" anlamına gelir türü nesneler için bir özel tanım sağlamak için aşırı yüklenmiş, ancak yalnızca bunları kullanın. Sınıfı ayrıca uygulayabilir <xref:System.IEquatable%601> arabirimi veya <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi. İki arabirim, değer eşitliği test etmek için kullanılan yöntemler sağlar. Ne zaman kendi tasarlama izin ver sınıfları bu geçersiz kılma `Equals`, belirtilen yönergeleri takip edin [nasıl yapılır: Tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Olaylar](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [object](../../../csharp/language-reference/keywords/object.md)
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
- [new İşleci](../../../csharp/language-reference/keywords/new-operator.md)
- [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md)
