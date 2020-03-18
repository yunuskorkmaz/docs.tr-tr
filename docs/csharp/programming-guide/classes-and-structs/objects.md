---
title: Nesneler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 09b290713f3bc2a7a7824bb19c98138943ad5b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673387"
---
# <a name="objects-c-programming-guide"></a>Nesneler (C# Programlama Kılavuzu)
Sınıf veya yapı tanımı, türün neler yapabileceğini belirten bir plan gibidir. Bir nesne temelde plana göre ayrılmış ve yapılandırılan bir bellek bloğudur. Bir program aynı sınıftan birçok nesne oluşturabilir. Nesnelere örnek olarak da adlandırılır ve adlandırılmış bir değişkende veya bir dizi veya koleksiyonda depolanabilirler. İstemci kodu, yöntemleri çağırmak ve nesnenin ortak özelliklerine erişmek için bu değişkenleri kullanan koddur. C# gibi nesne yönelimli bir dilde, tipik bir program dinamik olarak etkileşimedebilen birden çok nesneden oluşur.  
  
> [!NOTE]
> Statik türleri burada açıklanandan farklı davranın. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.
  
## <a name="struct-instances-vs-class-instances"></a>Struct Örnekleri ve Sınıf Örnekleri  
 Sınıflar başvuru türleri olduğundan, sınıf nesnesinin değişkeni yönetilen yığındaki nesnenin adresine başvuruda bulundu. İlk nesneye aynı türden ikinci bir nesne atanmışsa, her iki değişken de bu adresteki nesneye başvurur. Bu nokta daha sonra bu konuda daha ayrıntılı olarak ele alınmıştır.  
  
 Sınıf örnekleri [yeni işleç](../../language-reference/operators/new-operator.md)kullanılarak oluşturulur. Aşağıdaki örnekte, `Person` türü ve `person1` `person 2` örnekleri veya nesneleri, bu tür.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Yapı türleri değer türleri olduğundan, bir yapı nesnesinin değişkeni tüm nesnenin bir kopyasını tutar. `new` İşleç kullanılarak da yapı örnekleri oluşturulabilir, ancak aşağıdaki örnekte gösterildiği gibi bu gerekli değildir:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Her ikisi `p1` için `p2` bellek ve iş parçacığı yığını üzerinde ayrılır. Bu bellek, beyan edildiği tür veya yöntemle birlikte geri alınır. Bu, yapıların atamada kopyalanmasının nedenlerinden biridir. Bunun aksine, bir sınıf örneği için ayrılan bellek, nesneye yapılan tüm başvurular kapsam dışına çıktığında ortak dil çalışma süresi tarafından otomatik olarak geri alınır (çöp toplanır). C++'da yaptığınız gibi bir sınıf nesnesini deterministically yok etmek mümkün değildir. .NET Framework'de çöp toplama hakkında daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.  
  
> [!NOTE]
> Yönetilen yığındaki belleğin tahsisi ve deallocation'ı ortak dil çalışma zamanında son derece iyi leştirilmiştir. Çoğu durumda yığında bir sınıf örneğini ayırmanın performans maliyetinde, yığına bir yapı örneği ayırmanın karşı sıcağı sıcağısı önemli bir fark yoktur.
  
## <a name="object-identity-vs-value-equality"></a>Nesne Kimliği ve Değer Eşitliği  
 Eşitlik için iki nesneyi karşılaştırdığınızda, öncelikle iki değişkenin bellekte aynı nesneyi temsil edip etmediğini veya bir veya daha fazla alanının değerlerinin eşdeğer olup olmadığını ayırt etmeniz gerekir. Değerleri karşılaştırmak istiyorsanız, nesnelerin değer türleri (yapı türleri) veya başvuru türleri (sınıflar, temsilciler, diziler) örnekleri olup olmadığını göz önünde bulundurmanız gerekir.  
  
- İki sınıf örneğinin bellekte aynı konuma başvurup başvurmadığını (yani aynı *kimliğe*sahip olduklarını) belirlemek için statik <xref:System.Object.Equals%2A> yöntemi kullanın. (<xref:System.Object?displayProperty=nameWithType> kullanıcı tanımlı yapı ve sınıflar da dahil olmak üzere tüm değer türleri ve başvuru türleri için örtük taban sınıftır.)  
  
- İki yapı örneğindeki örnek alanlarının aynı değerlere sahip olup <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> olmadığını belirlemek için yöntemi kullanın. Tüm yapılardan dolaylı olarak devraldığı <xref:System.ValueType?displayProperty=nameWithType>için, yöntemi aşağıdaki örnekte gösterildiği gibi doğrudan nesnenize çağırırsınız:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 Herhangi <xref:System.ValueType?displayProperty=nameWithType> bir `Equals` yapıda alanların ne olduğunu belirleyebilmesi gerektiğinden yansımanın uygulanması. Kendi yapılarınızı oluştururken, türünüze `Equals` özgü verimli bir eşitlik algoritması sağlamak için yöntemi geçersiz kılın.  
  
- İki sınıf örneğindeki alanların değerlerinin eşit olup olmadığını belirlemek için <xref:System.Object.Equals%2A> yöntemi veya [== işlecik'i](../../language-reference/operators/equality-operators.md#equality-operator-)kullanabilirsiniz. Ancak, yalnızca sınıf bunları geçersiz kılmış veya aşırı yüklemişse, "eşitlik"in bu tür nesneler için ne anlama geldiğinin özel bir tanımını sağlamak için kullanın. Sınıf, <xref:System.IEquatable%601> arabirimi veya <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi de uygulayabilir. Her iki arabirim de değer eşitliğini sınamak için kullanılabilecek yöntemler sağlar. Geçersiz kılınan `Equals`kendi sınıflarınızı tasarlarken, bir tür ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>değer [eşitliğini nasıl tanımlarsınız'da](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) belirtilen yönergelere uyduğunuzdan emin olun.
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Sınıflar](./classes.md)  
  
- [Oluşturucular](./constructors.md)  
  
- [Sonlandırıcılar](./destructors.md)  
  
- [Olaylar](../events/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne](../../language-reference/builtin-types/reference-types.md)
- [Devralma](./inheritance.md)
- [Sınıfı](../../language-reference/keywords/class.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [new İşleci](../../language-reference/operators/new-operator.md)
- [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md)
