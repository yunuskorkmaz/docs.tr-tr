---
title: Devralma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 6294669a05f5cc6c52de5164d89e29062ceb6bdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323608"
---
# <a name="inheritance-c-programming-guide"></a>Devralma (C# Programlama Kılavuzu)

Saklama ve çok biçimlilik, birlikte devralma nesne odaklı programlama üç birincil özelliklerini biridir. Devralma yeniden genişletmek ve diğer sınıflarda tanımlanan davranışını yeni sınıflar oluşturmanızı sağlar. Üyeleri devralındığı sınıfı adlı *temel sınıfı*, bu üyeler devralan sınıf adı verilen ve *türetilmiş sınıf*. Türetilmiş bir sınıf doğrudan yalnızca bir temel sınıf olabilir. Ancak, devralma geçişli olur. ClassC ClassB türetilmiş ve ClassB ClassA türetilmiş, ClassC ClassB ve ClassA bildirilen üyeleri devralır.  
  
> [!NOTE]
>  Yapılar devralma desteklemez, ancak arabirimleri uygulayabilir. Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
 Kavramsal olarak, türetilmiş bir sınıf temel sınıfın uzmanlık ' dir. Örneğin, bir taban sınıf varsa `Animal`, adlı bir türetilmiş sınıf olabilir `Mammal` ve adlı başka bir türetilmiş sınıf `Reptile`. A `Mammal` olan bir `Animal`ve bir `Reptile` olan bir `Animal`, ancak her türetilmiş bir sınıf temel sınıfın farklı özelleştirmeleri temsil eder.  
  
 Başka bir sınıftan türeyen bir sınıf tanımladığınızda, türetilmiş sınıf oluşturucular ve sonlandırıcılar dışında temel sınıfın tüm üyeleri örtük olarak kazanır. Türetilmiş sınıf yeniden uygulamak zorunda kalmadan temel sınıfı kodda böylece yeniden kullanabilirsiniz. Türetilen sınıfta daha fazla üye ekleyebilir. Bu şekilde, türetilen sınıfın temel sınıf işlevselliğini genişletir.  
  
 Aşağıdaki çizimde bir sınıfı göstermektedir `WorkItem` , bazı iş sürecini iş bir öğeyi temsil eder. Öğesinden türetilen tüm sınıflar gibi <xref:System.Object?displayProperty=nameWithType> ve tüm yöntemleri devralır. `WorkItem` beş üyeleri kendi ekler. Oluşturucular devralınmaz çünkü bunlar bir oluşturucu içerir. Sınıf `ChangeRequest` devraldığı `WorkItem` ve belirli bir iş öğesi türünü temsil eder. `ChangeRequest` öğesinden devralınan üyeler iki daha fazla üye ekler `WorkItem` ve <xref:System.Object>. Kendi Oluşturucusu eklemeniz gerekir ve ayrıca ekler `originalItemID`. Özellik `originalItemID` sağlayan `ChangeRequest` özgün ile ilişkilendirilecek örneği `WorkItem` değişiklik isteğini geçerli olduğu için.  
  
 ![Sınıf devralma](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Sınıf devralma  
  
 Aşağıdaki örnekte nasıl önceki çizimde gösterilen sınıf ilişkileri C# ' ta belirtilmiştir gösterir. Bu örnek ayrıca gösterir nasıl `WorkItem` sanal yöntemini geçersiz kılar <xref:System.Object.ToString%2A?displayProperty=nameWithType>ve nasıl `ChangeRequest` sınıfının devraldığı `WorkItem` yöntemin kullanımı.  
  
 [!code-csharp[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemleri  
 Ne zaman bir taban sınıf bildiren bir yöntem olarak [sanal](../../../csharp/language-reference/keywords/virtual.md), türetilmiş sınıf [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) kendi uygulama yöntemiyle. Bir temel sınıf olarak bir üye bildirirse [soyut](../../../csharp/language-reference/keywords/abstract.md), doğrudan bu sınıfından devralan tüm soyut olmayan sınıfı içinde yöntemi geçersiz kılınmalıdır. Türetilmiş bir sınıf kendisi ise soyut, soyut üyelerini uygulamadan devralır. Soyut ve sanal çok biçimlilik, temel nesne odaklı programlama ikinci birincil özelliği olduğu üyeleridir. Daha fazla bilgi için bkz: [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Soyut taban sınıfları  
 Bir sınıf olarak bildirebilir [soyut](../../../csharp/language-reference/keywords/abstract.md) kullanarak doğrudan engellemek istiyorsanız [yeni](../../../csharp/language-reference/keywords/new.md) anahtar sözcüğü. Bunu yaparsanız, yalnızca yeni bir sınıf türetilmiş sınıf kullanılabilir. Bir Özet sınıf bir içerebilir veya daha fazla yöntem imzaları, kendilerini soyut olarak bildirilir. Bu imzaları parametreleri belirtin ve dönüş değeri ancak hiçbir uygulaması (yöntem gövdesi) sahip. Bir Özet Sınıf soyut üyelerini içeren gerekmez; Ancak, bir sınıf soyut bir üye içeriyorsa, bu sınıfı soyut olarak bildirilmesi gerekir. Soyut olmayan türetilen sınıflar kendilerini bir soyut taban sınıfından herhangi bir Özet yöntem uygulamasını sağlamanız gerekir. Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Arabirimler  
 Bir *arabirimi* yalnızca soyut üyeleri oluşan bir Özet temel sınıf için biraz benzer bir başvuru türüdür. Bir sınıf bir arabirimini uygulayan, arabirimin tüm üyeleri için bir uygulama sağlaması gerekir. Bu yalnızca bir tek doğrudan taban sınıfından türetilen olsa da bir sınıf birden çok arabirimi uygulayabilirsiniz.  
  
 Arabirimleri mutlaka olmadığı sınıfları için belirli özelliklerini tanımlamak için kullanılan bir "olan bir" ilişki. Örneğin, <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi herhangi bir sınıf veya (ancak türü eşdeğer tanımlar) türde iki nesne eşdeğer olup olmadığını belirlemek istemci kodu etkinleştirmek için sahip yapısı tarafından uygulanabilir. <xref:System.IEquatable%601> aynı tür göstermez "olan bir" temel sınıf ve türetilmiş bir sınıf arasında var ilişkisi (örneğin, bir `Mammal` olan bir `Animal`). Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Daha fazla türetme önleme  
 Bir sınıf dışarı ya da, bu grubun üyeleri herhangi kendisini veya üye olarak bildirerek öğesinden devralan diğer sınıflara engelleyebilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md). Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Taban sınıfı üyeleri türetilmiş sınıf gizleme  
 Türetilmiş bir sınıf, aynı ad ve imza üyeleriyle bildirerek taban sınıfı üyeleri gizleyebilirsiniz. [Yeni](../../../csharp/language-reference/keywords/new.md) değiştiricisi üye bir geçersiz kılma temel üyesinin olması amaçlanmamıştır açıkça belirtmek için kullanılabilir. Kullanımını [yeni](../../../csharp/language-reference/keywords/new.md) gerekli değildir ancak derleyici uyarısı oluşturulan [yeni](../../../csharp/language-reference/keywords/new.md) kullanılmaz. Daha fazla bilgi için bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [kullanımı geçersiz kılma ve yeni anahtar sözcüklerin için bilerek olduğunda](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)
