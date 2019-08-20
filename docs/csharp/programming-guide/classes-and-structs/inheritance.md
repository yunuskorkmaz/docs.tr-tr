---
title: Devralma- C# Programlama Kılavuzu
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
ms.openlocfilehash: 1fc8303ad4d54bfd3255d725de486281cd09439e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596557"
---
# <a name="inheritance-c-programming-guide"></a>Devralma (C# Programlama Kılavuzu)

Kapsülleme ve çok biçimlilik ile birlikte devralma, nesne odaklı programlamanın üç birincil özelliklerinden biridir. Devralma, diğer sınıflarda tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni sınıflar oluşturmanıza olanak sağlar. Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir. Türetilmiş bir sınıfın yalnızca bir doğrudan temel sınıfı olabilir. Ancak, devralma geçişlidir. ClassC, ClassB 'den türetildiyse ve ClassB, ClassA 'dan türetilirse ClassC, ClassB ve ClassA 'da belirtilen üyeleri devralır.  
  
> [!NOTE]
>  Yapılar devralmayı desteklemez, ancak arabirimler uygulayabilir. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
 Kavramsal olarak, türetilmiş bir sınıf temel sınıfın bir özelleştirmesi olur. Örneğin, bir taban sınıfınız `Animal`varsa adlı bir türetilmiş sınıfa `Mammal` ve adında `Reptile`başka bir türetilmiş sınıfa sahip olabilirsiniz. , Bir, `Reptile` ve bir olur ,ancakhertüretilmişsınıftemelsınıfınfarklıözelleştirmelerinitemsileder.`Animal` `Mammal` `Animal`  
  
 Başka bir sınıftan türetmek için bir sınıf tanımladığınızda, türetilmiş sınıf, oluşturucular ve sonlandırıcılar hariç, temel sınıfın tüm üyelerini dolaylı olarak kazanıyor. Türetilmiş sınıf bundan sonra kodu yeniden uygulamak zorunda kalmadan temel sınıfta yeniden kullanabilir. Türetilmiş sınıfta daha fazla üye ekleyebilirsiniz. Bu şekilde, türetilmiş sınıf temel sınıfın işlevselliğini genişletir.  
  
 Aşağıdaki çizimde, bazı iş sürecindeki `WorkItem` bir iş öğesini temsil eden bir sınıf gösterilmektedir. Tüm sınıflar gibi, öğesinden <xref:System.Object?displayProperty=nameWithType> türetilir ve tüm yöntemlerini devralır. `WorkItem`kendisine ait beş üyeyi ekler. Bunlar bir Oluşturucu içerir, çünkü oluşturucular devralınmaz. Sınıf `ChangeRequest` öğesinden`WorkItem` devralır ve belirli bir iş öğesi türünü temsil eder. `ChangeRequest`devralınan `WorkItem` üyelere ve kaynağından <xref:System.Object>daha fazla üye ekler. Kendi oluşturucusunu eklemesi ve ayrıca eklemesi `originalItemID`gerekir. Özelliği `originalItemID` , `ChangeRequest` Örneğin değişiklik isteğinin uygulandığı orijinalle `WorkItem` ilişkilendirilmesini sağlar.  
  
 ![Sınıf devralmayı gösteren diyagram](./media/inheritance/class-inheritance-diagram.png)  
  
 Aşağıdaki örnek, önceki çizimde gösterilen sınıf ilişkilerinin ' de C#nasıl ifade edildiği gösterilmektedir. `WorkItem` Örnek ayrıca sanal yöntemin <xref:System.Object.ToString%2A?displayProperty=nameWithType>nasıl geçersiz kılındığını ve `ChangeRequest` sınıfın yöntem `WorkItem` uygulamasını nasıl devraldığını gösterir.  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemler  
 Bir temel sınıf bir yöntemi [sanal](../../language-reference/keywords/virtual.md)olarak bildiriyorsa, türetilmiş bir sınıf yöntemi kendi uygulamasıyla [geçersiz kılabilir](../../language-reference/keywords/override.md) . Bir temel sınıf bir üyeyi [soyut](../../language-reference/keywords/abstract.md)olarak bildiriyorsa, bu yöntemin doğrudan bu sınıftan devralan Özet olmayan herhangi bir sınıfta geçersiz kılınmalıdır. Türetilmiş bir sınıf kendi soyut ise, soyut üyeleri Uygulamasız devralır. Soyut ve sanal üyeler, nesne odaklı programlamanın ikinci birincil özelliği olan çok biçimlilik için temeldir. Daha fazla bilgi için bkz. çok [biçimlilik](./polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Soyut temel sınıflar  
 [New](../../language-reference/operators/new-operator.md) işlecini kullanarak doğrudan örnek oluşturmayı engellemek istiyorsanız, bir sınıfı [soyut](../../language-reference/keywords/abstract.md) olarak bildirebilirsiniz. Bunu yaparsanız, sınıfı yalnızca yeni bir sınıf ondan türetilirse kullanılabilir. Soyut bir sınıf, kendilerine soyut olarak bildirildiği bir veya daha fazla yöntem imzası içerebilir. Bu imzalar parametreleri ve dönüş değerini belirtir, ancak hiçbir uygulamaya (Yöntem gövdesi) sahip olmaz. Soyut bir sınıfın soyut Üyeler içermesi gerekmez; Ancak, bir sınıf soyut üye içeriyorsa, sınıfın kendisi Özet olarak bildirilmelidir. Soyut olmayan türetilmiş sınıfların, soyut bir temel sınıftan herhangi bir soyut Yöntem için uygulama sağlaması gerekir. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Arabirimler  
 *Arabirim* , yalnızca soyut üyelerden oluşan soyut temel sınıfa benzer bir başvuru türüdür. Bir sınıf bir arabirim uygularsa, arabirimin tüm üyeleri için bir uygulama sağlamalıdır. Bir sınıf, yalnızca tek bir doğrudan taban sınıftan türeyebilse de birden çok arabirim uygulayabilir.  
  
 Arabirimler, "bir" a "ilişkisine sahip olmayan sınıflar için belirli özellikleri tanımlamak üzere kullanılır. Örneğin, <xref:System.IEquatable%601?displayProperty=nameWithType> arabirim, tür iki nesnenin eşdeğer olup olmadığını belirlemesi için istemci kodunu etkinleştirmek zorunda olan herhangi bir sınıf veya yapı tarafından uygulanabilir (ancak tür denklik tanımlar). <xref:System.IEquatable%601>, bir temel sınıf ve türetilmiş bir sınıf (örneğin, a `Mammal` `Animal`) arasında bulunan aynı "bir" ilişki türünü göstermez. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Daha fazla türetme engelleniyor  
 Bir sınıf, kendisini veya üyeyi [korumalı](../../language-reference/keywords/sealed.md)olarak bildirerek diğer sınıfların bunlardan veya üyelerinden birinden devralmasını önleyebilir. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Temel sınıf üyelerinin türetilmiş sınıf gizlemesi  
 Türetilmiş bir sınıf, aynı ada ve imzaya sahip üyeleri bildirerek, temel sınıf üyelerini gizleyebilir. [Yeni](../../language-reference/keywords/new-modifier.md) değiştirici, üyenin temel üyenin geçersiz kılınmasına yönelik amaçlanmadığını açıkça belirtmek için kullanılabilir. [Yeni](../../language-reference/keywords/new-modifier.md) kullanımı gerekli değildir, ancak [Yeni](../../language-reference/keywords/new-modifier.md) kullanılmazsa derleyici uyarısı oluşturulacaktır. Daha fazla bilgi için bkz. geçersiz kılma ve [Yeni anahtar sözcüklerle sürüm oluşturma](./versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
