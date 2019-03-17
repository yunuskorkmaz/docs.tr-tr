---
title: Devralma - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 9ad7253fb9efc891e1f0fdea118e1fe7bde6a857
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125921"
---
# <a name="inheritance-c-programming-guide"></a>Devralma (C# Programlama Kılavuzu)

Devralma, kapsülleme ve çok biçimlilik, birlikte üç birincil nesne yönelimli programlama özelliklerini biridir. Devralma, yeniden, genişleten ve diğer sınıflarında tanımlanan davranışını değiştiren yeni sınıflar oluşturmanıza olanak sağlar. Üyeleri devralınan sınıf *temel sınıfı*, ve bu üyeleri devralan sınıf *türetilmiş sınıf*. Türetilmiş bir sınıf yalnızca bir doğrudan taban sınıfı olabilir. Ancak, devralma geçişli değildir. Önce Sınıfc Sınıfb ' türetilir ve Sınıfb Türetilme türetilir, önce Sınıfc da sınıfa Sınıfb ile bildirilen üyelerini devralır.  
  
> [!NOTE]
>  Yapılar devralımı desteklemez, ancak arabirimleri uygulayabilir. Daha fazla bilgi için [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
 Kavramsal olarak, türetilmiş bir sınıf temel sınıfın bir özelleştirmesi ' dir. Örneğin, bir temel sınıf varsa `Animal`, adlı bir türetilmiş sınıf olabilir `Mammal` ve adlı başka bir türetilmiş sınıf `Reptile`. A `Mammal` olduğu bir `Animal`ve `Reptile` olduğu bir `Animal`, ancak her türetilen sınıf temel sınıfın farklı uzmanlıklar temsil eder.  
  
 Başka bir sınıftan türetilen bir sınıf tanımladığınızda, türetilmiş sınıf oluşturucu ve sonlandırıcılar hariç temel sınıfın tüm üyeleri örtük olarak kazanır. Türetilmiş sınıf yeniden uygulamak zorunda kalmadan kod temel sınıfta başvurulabilir, böylece yeniden kullanabilirsiniz. Türetilen bir sınıfta, daha fazla üye ekleyebilirsiniz. Bu şekilde, türetilen sınıfın temel sınıf işlevselliğini genişletir.  
  
 Bir sınıf aşağıdaki çizimde `WorkItem` , bazı iş sürecini iş bir öğeyi temsil eder. Öğesinden türetilen tüm sınıflar gibi <xref:System.Object?displayProperty=nameWithType> ve tüm yöntemleri alır. `WorkItem` beş üyeleri kendi ekler. Oluşturucular devralınmaz çünkü bunlar bir oluşturucu içerir. Sınıf `ChangeRequest` devraldığı `WorkItem` ve belirli bir iş öğesi türünü temsil eder. `ChangeRequest` öğesinden devralınan üyelere iki daha fazla üye ekleyen `WorkItem` ve <xref:System.Object>. Kendi Oluşturucusu eklemelisiniz ve ayrıca ekler `originalItemID`. Özellik `originalItemID` sağlayan `ChangeRequest` özgün ile ilişkilendirilecek örneği `WorkItem` değişiklik isteğini geçerli olduğu için.  
  
 ![Sınıf devralma gösteren diyagram](./media/inheritance/class-inheritance-diagram.png)  
  
 Aşağıdaki örnek nasıl önceki resimde gösterilen ilişkileri C# dilinde ifade edildiğini gösterir. Örnek ayrıca gösterir nasıl `WorkItem` sanal yöntemini geçersiz kılan <xref:System.Object.ToString%2A?displayProperty=nameWithType>ve nasıl `ChangeRequest` sınıfından devralan `WorkItem` yöntemi.  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemleri  
 Ne zaman bir taban sınıfı yöntemi olarak bildirir [sanal](../../../csharp/language-reference/keywords/virtual.md), türetilmiş sınıf [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) kendi uygulaması ile yöntemi. Bir temel sınıf üyesi olarak bildirirse [soyut](../../../csharp/language-reference/keywords/abstract.md), doğrudan bu sınıftan devralınan tüm soyut olmayan sınıf içinde yöntemi geçersiz kılınmalıdır. Türetilmiş bir sınıf kendisi ise soyut, soyut üye uygulamadan devralır. Soyut ve sanal çok biçimlilik, temel nesne yönelimli programlama, ikinci birincil özelliği olduğu üyeleridir. Daha fazla bilgi için [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Soyut taban sınıfları  
 Bir sınıf olarak bildirebilirsiniz [soyut](../../../csharp/language-reference/keywords/abstract.md) kullanarak doğrudan engellemek istiyorsanız [yeni](../../../csharp/language-reference/keywords/new.md) anahtar sözcüğü. Bunu yaparsanız, yalnızca yeni bir sınıf buradan cdocument'tan türetilirse sınıfı kullanılabilir. Bir Özet sınıf, bir veya daha fazla yöntem imzaları, kendilerini soyut olarak bildirilir. Bu imza parametreleri belirtin ve dönüş değeri ancak (yöntem gövdesi) uygulaması bulunmuyor. Bir soyut sınıfı soyut üye içermesi gerekmez; Ancak, bir sınıf, soyut bir üye içeriyorsa, sınıfı soyut olarak bildirilmelidir. Soyut olmayan türetilmiş sınıfları tüm soyut yöntemler soyut bir temel sınıftan uygulamasını kendilerini sağlamanız gerekir. Daha fazla bilgi için [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Arabirimler  
 Bir *arabirimi* oluşur yalnızca soyut üye bir soyut temel sınıf için biraz benzer bir başvuru türüdür. Bir sınıf bir arabirimi uygulayan, arabirimin tüm üyeleri için bir uygulama sağlamalıdır. Bu yalnızca bir tek doğrudan temel sınıftan türetilen olsa bile bir sınıf birden fazla arabirim uygulayabilir.  
  
 Arabirimleri mutlaka sahip olmayan sınıflar için belirli özelliklerini tanımlamak için kullanılan bir "olan bir" ilişkisi. Örneğin, <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimi herhangi bir sınıfın veya vardır (ancak türü eşdeğerlik tanımlar) türünden iki nesne eşdeğer olup olmadığını belirlemek istemci kodu etkinleştirmek için yapı tarafından uygulanabilir. <xref:System.IEquatable%601> aynı tür gelmez "olan bir" temel sınıf ve türetilen sınıf arasında bir ilişki (örneğin, bir `Mammal` olduğu bir `Animal`). Daha fazla bilgi için [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Daha fazla türetme önleme  
 Bir sınıfı diğer sınıflar bu veya herhangi bir grubun üyeleri kendisini veya üye olarak bildirerek devralmasını engelleyebilirsiniz [korumalı](../../../csharp/language-reference/keywords/sealed.md). Daha fazla bilgi için [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Temel sınıf üyelerinin türetilmiş sınıf gizleme  
 Türetilmiş bir sınıf, taban sınıfı üyeleri aynı ada ve imzaya sahip üyeler bildirerek gizleyebilirsiniz. [Yeni](../../../csharp/language-reference/keywords/new.md) değiştiricisi üye, temel üyeyi geçersiz kılma olacak şekilde tasarlanmamıştır açıkça belirtmek için kullanılabilir. Kullanımını [yeni](../../../csharp/language-reference/keywords/new.md) gerekli değildir, ancak bir derleyici uyarısı oluşturulur [yeni](../../../csharp/language-reference/keywords/new.md) kullanılmaz. Daha fazla bilgi için [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [bilerek, kullanım geçersiz kılma ve yeni anahtar sözcüklerle](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
