---
title: Nesneler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: a2f5300f9647823cf2c9ac2a4a5c7c888c7dd245
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626587"
---
# <a name="objects-c-programming-guide"></a>Nesneler (C# Programlama Kılavuzu)
Sınıf veya yapı tanımı, türün ne yapabileceğini belirten bir şema gibidir. Bir nesne temelde, Blueprint 'e göre ayrılan ve yapılandırılan bir bellek bloğudur. Bir program aynı sınıftan birçok nesne oluşturabilir. Nesneler de örnekler olarak adlandırılır ve adlandırılmış bir değişkende veya bir dizi ya da koleksiyonda depolanabilir. İstemci kodu, yöntemleri çağırmak ve nesnenin ortak özelliklerine erişmek için bu değişkenleri kullanan koddur. Gibi nesne yönelimli bir dilde C#, tipik bir program dinamik olarak etkileşimde bulunan birden çok nesneden oluşur.  
  
> [!NOTE]
> Statik türler burada açıklananla farklı davranır. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Struct örnekleri ve sınıf örnekleri  
 Sınıflar başvuru türleri olduğundan, sınıf nesnesinin bir değişkeni yönetilen yığında nesnenin adresine bir başvuru içerir. Aynı türde ikinci bir nesne ilk nesnesine atanırsa, her iki değişken de o adresteki nesneye başvurur. Bu nokta, bu konunun ilerleyen kısımlarında daha ayrıntılı bir şekilde ele alınmıştır.  
  
 Sınıfların örnekleri, [New işleci](../../language-reference/operators/new-operator.md)kullanılarak oluşturulur. Aşağıdaki örnekte, `Person` tür ve `person1` ve bu türdeki `person 2` örnekler ya da nesnelerdir.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Yapılar değer türleri olduğundan, bir struct nesnesinin değişkeni tüm nesnenin bir kopyasını tutar. Yapı örnekleri, `new` işleci kullanılarak da oluşturulabilir, ancak aşağıdaki örnekte gösterildiği gibi bu gerekli değildir:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Hem `p1` hem de `p2` için bellek, iş parçacığı yığınında ayrılır. Bu bellek, bildirildiği tür veya yöntem ile birlikte geri kazanılır. Bu, yapıların atama sırasında kopyalanmasının bir nedenidir. Buna karşılık, bir sınıf örneği için ayrılan bellek, nesneye yapılan tüm başvurular kapsam dışına çıkış yaparken ortak dil çalışma zamanı tarafından otomatik olarak geri kazanılır (çöp toplamıştır). İçinde C++yaptığınız gibi bir sınıf nesnesini kesin şekilde yok etmek mümkün değildir. .NET Framework çöp toplama hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Yönetilen yığında bellek ayırma ve ayırmayı kaldırma işlemi, ortak dil çalışma zamanında son derece iyileştirilmiştir. Çoğu durumda, yığında bir sınıf örneği ayırmanın performans maliyetinde önemli bir fark yoktur.
  
## <a name="object-identity-vs-value-equality"></a>Nesne kimliği ve değer eşitlik karşılaştırması  
 İki nesneyi eşitlik için karşılaştırdığınızda, ilk olarak iki değişkenin bellekte aynı nesneyi temsil ettiğini veya bir ya da daha fazla alanının değerlerinin eşdeğer olup olmadığını ayırt etmeniz gerekir. Değerleri karşılaştırmak istiyorsanız, nesnelerin değer türleri (yapılar) veya başvuru türleri (sınıflar, temsilciler, diziler) örnekleri olup olmadığını göz önünde bulundurmanız gerekir.  
  
- İki sınıf örneğinin bellekteki aynı konuma (aynı *kimliğe*sahip oldukları anlamına gelir) başvuruda bulunup bulunmadığını anlamak için, statik <xref:System.Object.Equals%2A> yöntemini kullanın. (<xref:System.Object?displayProperty=nameWithType>, Kullanıcı tanımlı yapılar ve sınıflar da dahil olmak üzere tüm değer türleri ve başvuru türleri için örtülü temel sınıftır.)  
  
- İki yapı örneğindeki örnek alanlarının aynı değerlere sahip olup olmadığını anlamak için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemini kullanın. Tüm yapılar <xref:System.ValueType?displayProperty=nameWithType>örtük olarak devraldığı için, aşağıdaki örnekte gösterildiği gibi yöntemi doğrudan nesneniz üzerinde çağırın:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 `Equals` <xref:System.ValueType?displayProperty=nameWithType> uygulanması, alanların herhangi bir yapıda olduğunu belirleyebilmesi gerektiği için yansıma kullanır. Kendi yapı birimlerinizi oluştururken, türüne özgü etkili bir eşitlik algoritması sağlamak için `Equals` yöntemini geçersiz kılın.  
  
- İki sınıf örneklerindeki alanların değerlerinin eşit olup olmadığını anlamak için <xref:System.Object.Equals%2A> yöntemini veya [= = işlecini](../../language-reference/operators/equality-operators.md#equality-operator-)kullanabilirsiniz. Ancak, yalnızca sınıf geçersiz kılınmışsa veya bu tür nesneler için "eşitlik" anlamına gelen özel bir tanım sağlamak için bunları aşırı yüklediyseniz kullanın. Sınıfı, <xref:System.IEquatable%601> arabirimini veya <xref:System.Collections.Generic.IEqualityComparer%601> arabirimini de uygulayabilir. Her iki arabirim de değer eşitliğini test etmek için kullanılabilecek yöntemler sağlar. `Equals`geçersiz kılan kendi sınıflarınızı tasarlarken, [bir tür ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>için değer eşitliği tanımlama](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) bölümünde belirtilen yönergeleri izlediğinizden emin olun.
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Sınıflar](./classes.md)  
  
- [Yapılar](./structs.md)  
  
- [Oluşturucular](./constructors.md)  
  
- [Sonlandırıcılar](./destructors.md)  
  
- [Olaylar](../events/index.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [object](../../language-reference/builtin-types/reference-types.md)
- [Devralma](./inheritance.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [new İşleci](../../language-reference/operators/new-operator.md)
- [Ortak Tür Sistemi](../../../standard/base-types/common-type-system.md)
