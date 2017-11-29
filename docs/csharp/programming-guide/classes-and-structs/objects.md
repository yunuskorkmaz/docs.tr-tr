---
title: "Nesneler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8a8e283b42b27a40780068be42c03fc5047a511
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="objects-c-programming-guide"></a>Nesneler (C# Programlama Kılavuzu)
Bir sınıf veya yapı türü neler yapabileceğinizi belirten şeması gibi tanımıdır. Bir nesne temelde ayrılmış ve şeması göre yapılandırılmış bellek bloğudur. Bir program aynı sınıfın birçok nesne oluşturabilir. Nesnelerin örneklerini de denir ve bir adlandırılmış değişkeninde veya bir dizi ya da koleksiyon depolanabilir. İstemci, bu değişkenleri yöntemlerini çağırın ve nesneyi genel özelliklerine erişmek için kullandığı kodu kodudur. Bir nesne yönelimli dil C# gibi tipik bir program dinamik olarak etkileşim birden çok nesnelerin oluşur.  
  
> [!NOTE]
>  Statik türleri burada açıklanan daha farklı şekilde davranır. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Yapı örnekleri vs. Sınıf örnekleri  
 Sınıflar başvuru türleri olduğundan, bir sınıf nesnesi bir değişken nesne adresine başvuru yönetilen yığında tutar. İlk nesneyi ikinci nesneden aynı türde atanırsa, her iki değişken adresi nesnede başvurun. Bu nokta, bu konunun ilerleyen bölümlerinde daha ayrıntılı ele alınmıştır.  
  
 Sınıfların örneklerini kullanarak oluşturulur [yeni işleç](../../../csharp/language-reference/keywords/new-operator.md). Aşağıdaki örnekte, `Person` türü ve `person1` ve `person 2` örnekleri ya da nesnelerin türü.  
  
 [!code-csharp[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Yapılar değer türleri olduğundan, bir değişken yapısı nesnesinin tüm nesnesinin bir kopyasını tutar. Yapılar örneklerini de oluşturulabilir kullanarak `new` işleci, ancak bu zorunlu değildir, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 Her ikisi için de bellek `p1` ve `p2` iş parçacığı yığında ayrılmış. Bu bellek türü veya yöntemi içinde bildirilmiş birlikte alınmadan. Yapılar atamada neden kopyalanır bir neden de budur. Nesne yapılan tüm başvuruları fazlası kapsam dışında aksine, bir sınıf örneği için ayrılan bellek (otomatik olarak geri çöp toplama) ortak dil çalışma zamanı tarafından durumdur. C++'ta yapabildiğiniz gibi bir sınıf nesnesi belirleyici biçimde yok etmek mümkün değildir. Çöp toplama hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bkz: [çöp toplama](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Ayırma ve yönetilen yığında bellek ayırmayı kaldırma ortak dil çalışma zamanı'nda yüksek oranda iyileştirilmiş. Çoğu durumda bir sınıf örneği yığında yapısı örneği ayırma karşı yığınındaki ayırma performans maliyetini önemli fark yoktur.  
  
## <a name="object-identity-vs-value-equality"></a>Nesne Kimliği vs. Değer eşitliği  
 İki nesnenin eşitlik için karşılaştırdığınızda olup bellek aynı nesne iki değişken temsil eder ve bir veya daha fazla alanlarının değerleri eşdeğer olup bilmek istediğinizi ilk ayırdetmek. Değerleri Karşılaştır amaçlanıyorsa nesneleri değer türleri (yapılar) veya başvuru türleri (sınıfları, temsilciler, diziler) örneği olup olmadığını dikkate almanız gerekir.  
  
-   İki sınıf örneklerini bellek aynı konumda başvurmak olup olmadığını belirlemek için (aynı sahip oldukları anlamına gelir *kimlik*), statik kullanmak <xref:System.Object.Equals%2A> yöntemi. (<xref:System.Object?displayProperty=nameWithType> tüm değer türleri ve başvuru türleri, kullanıcı tanımlı yapıları ve sınıfları dahil olmak üzere örtük temel sınıftır.)  
  
-   İki yapısı örneği örneği alanları aynı değerlere sahip olup olmadığını belirlemek için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi. Tüm yapılar örtük olarak öğesinden devraldığı <xref:System.ValueType?displayProperty=nameWithType>, doğrudan nesne üzerinde aşağıdaki örnekte gösterildiği gibi yöntemini çağırın:  
  
 [!code-csharp[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Uyarlamasını `Equals` herhangi yapıda alanlar nelerdir belirlemek mümkün olması nedeniyle yansıma kullanır. Kendi yapılar oluştururken, geçersiz kılma `Equals` türünüz için belirli bir verimli eşitlik algoritma sağlamak için yöntem.  
  
-   İki sınıf durumlarda alanlarına ait değerlerin eşit olup olmadığını belirlemek için kullanılacak olabilir <xref:System.Object.Equals%2A> yöntemi veya [== işleci](../../../csharp/language-reference/operators/equality-comparison-operator.md). Sınıf geçersiz veya bu türündeki nesneler için hangi "eşitlik" anlamına gelir, özel bir tanımını sağlamak için aşırı yüklü, ancak yalnızca kullanın. Sınıf ayrıca uygulayabilir <xref:System.IEquatable%601> arabirimi veya <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi. Her iki arabirimde değer eşitliği test etmek için kullanılan yöntemleri sağlar. Ne zaman kendi tasarlama izin ver sınıfları bu geçersiz kılma `Equals`, belirtilen yönergeleri izlediğinizden emin olun [nasıl yapılır: bir tür için değer eşitliği tanımlama](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Olayları](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne](../../../csharp/language-reference/keywords/object.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [sınıfı](../../../csharp/language-reference/keywords/class.md)  
 [yapısı](../../../csharp/language-reference/keywords/struct.md)  
 [New işleci](../../../csharp/language-reference/keywords/new-operator.md)  
 [Ortak tür sistemi](../../../standard/base-types/common-type-system.md)
