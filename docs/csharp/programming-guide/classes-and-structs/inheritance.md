---
title: Devralma-C# Programlama Kılavuzu
description: C# ' de devralma, diğer sınıflarda tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni sınıflar oluşturmanıza olanak sağlar.
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 6b94f58801af188655474f9c7de76b79381e721d
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864261"
---
# <a name="inheritance-c-programming-guide"></a>Devralma (C# Programlama Kılavuzu)

Kapsülleme ve çok biçimlilik ile birlikte devralma, nesne odaklı programlamanın üç birincil özelliklerinden biridir. Devralma, diğer sınıflarda tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni sınıflar oluşturmanıza olanak sağlar. Üyeleri devralınmış olan sınıfa *temel sınıf*denir ve bu üyeleri devralan sınıfa *türetilmiş sınıf*denir. Türetilmiş bir sınıfın yalnızca bir doğrudan temel sınıfı olabilir. Ancak, devralma geçişlidir. `ClassC`, Öğesinden türetildiyse `ClassB` ve `ClassB` öğesinden türetildiyse `ClassA` , ve ' `ClassC` de belirtilen üyeleri devralır `ClassB` `ClassA` .

> [!NOTE]
> Yapılar devralmayı desteklemez, ancak arabirimler uygulayabilir. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).

Kavramsal olarak, türetilmiş bir sınıf temel sınıfın bir özelleştirmesi olur. Örneğin, bir taban sınıfınız varsa adlı bir `Animal` türetilmiş sınıfa `Mammal` ve adında başka bir türetilmiş sınıfa sahip olabilirsiniz `Reptile` . `Mammal` `Animal` , Bir, ve bir `Reptile` olur `Animal` , ancak her türetilmiş sınıf temel sınıfın farklı özelleştirmelerini temsil eder.

Arabirim bildirimleri, üyeleri için varsayılan bir uygulama tanımlayabilir. Bu uygulamalar, türetilmiş arabirimler ve bu arabirimleri uygulayan sınıflar tarafından devralınır. Varsayılan arabirim yöntemleri hakkında daha fazla bilgi için, dil başvurusu bölümündeki [arabirimlerde](../../language-reference/keywords/interface.md) bulunan makaleye bakın.

Başka bir sınıftan türetmek için bir sınıf tanımladığınızda, türetilmiş sınıf, oluşturucular ve sonlandırıcılar hariç, temel sınıfın tüm üyelerini dolaylı olarak kazanıyor. Türetilmiş sınıf, kodu yeniden uygulamaya gerek kalmadan temel sınıfta yeniden kullanır. Türetilmiş sınıfa daha fazla üye ekleyebilirsiniz. Türetilmiş sınıf, temel sınıfın işlevselliğini genişletir.

Aşağıdaki çizimde, `WorkItem` bazı iş sürecindeki bir iş öğesini temsil eden bir sınıf gösterilmektedir. Tüm sınıflar gibi, öğesinden türetilir <xref:System.Object?displayProperty=nameWithType> ve tüm yöntemlerini devralır. `WorkItem`kendisine ait beş üyeyi ekler. Oluşturucular devroluşturulmadığından bu Üyeler bir Oluşturucu içerir. Sınıf `ChangeRequest` öğesinden devralır `WorkItem` ve belirli bir iş öğesi türünü temsil eder. `ChangeRequest`devralınan üyelere ve kaynağından daha fazla üye ekler `WorkItem` <xref:System.Object> . Kendi oluşturucusunu eklemesi ve ayrıca eklemesi gerekir `originalItemID` . Özelliği, `originalItemID` `ChangeRequest` Örneğin `WorkItem` değişiklik isteğinin uygulandığı orijinalle ilişkilendirilmesini sağlar.

![Sınıf devralmayı gösteren diyagram](./media/inheritance/class-inheritance-diagram.png)

Aşağıdaki örnek, önceki çizimde gösterilen sınıf ilişkilerinin C# dilinde nasıl ifade edildiği gösterilmektedir. Örnek ayrıca `WorkItem` sanal yöntemin nasıl geçersiz kılındığını <xref:System.Object.ToString%2A?displayProperty=nameWithType> ve `ChangeRequest` sınıfın yöntem uygulamasını nasıl devraldığını gösterir `WorkItem` . İlk blok sınıfları tanımlar:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Bu sonraki blok, temel ve türetilmiş sınıfların nasıl kullanılacağını gösterir:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemler

Bir temel sınıf olarak bir yöntemi bildiriyorsa [`virtual`](../../language-reference/keywords/virtual.md) , türetilmiş bir sınıf [`override`](../../language-reference/keywords/override.md) yöntemi kendi uygulamasına sahip olabilir. Bir temel sınıf olarak bir üye bildirirse [`abstract`](../../language-reference/keywords/abstract.md) , bu yöntemin doğrudan bu sınıftan devralan Özet olmayan herhangi bir sınıfta geçersiz kılınmalıdır. Türetilmiş bir sınıf kendi soyut ise, soyut üyeleri Uygulamasız devralır. Soyut ve sanal üyeler, nesne odaklı programlamanın ikinci birincil özelliği olan çok biçimlilik için temeldir. Daha fazla bilgi için bkz. çok [biçimlilik](./polymorphism.md).

## <a name="abstract-base-classes"></a>Soyut temel sınıflar

[New](../../language-reference/operators/new-operator.md) işlecini kullanarak doğrudan örnek oluşturmayı engellemek istiyorsanız, bir sınıfı [soyut](../../language-reference/keywords/abstract.md) olarak bildirebilirsiniz. Soyut bir sınıf, yalnızca yeni bir sınıf ondan türetilirse kullanılabilir. Soyut bir sınıf, kendilerine soyut olarak bildirildiği bir veya daha fazla yöntem imzası içerebilir. Bu imzalar parametreleri ve dönüş değerini belirtir, ancak hiçbir uygulamaya (Yöntem gövdesi) sahip olmaz. Soyut bir sınıfın soyut Üyeler içermesi gerekmez; Ancak, bir sınıf soyut üye içeriyorsa, sınıfın kendisi Özet olarak bildirilmelidir. Soyut olmayan türetilmiş sınıflar, soyut bir temel sınıftan herhangi bir soyut Yöntem için uygulama sağlamalıdır. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Arabirimler

*Arabirim* , bir üye kümesini tanımlayan bir başvuru türüdür. Bu arabirimi uygulayan tüm sınıfların ve yapıların bu üye kümesini uygulaması gerekir. Arabirim, bu üyelerin herhangi biri veya tümü için varsayılan bir uygulama tanımlayabilir. Bir sınıf, yalnızca tek bir doğrudan taban sınıftan türeyebilse de birden çok arabirim uygulayabilir.

Arabirimler, "bir" a "ilişkisine sahip olmayan sınıflar için belirli özellikleri tanımlamak üzere kullanılır. Örneğin, bu <xref:System.IEquatable%601?displayProperty=nameWithType> arabirim, türün iki nesnesinin eşdeğer olup olmadığını (ancak, tür denklik tanımlar) anlamak için herhangi bir sınıf veya yapı tarafından uygulanabilir. <xref:System.IEquatable%601>, bir temel sınıf ve türetilmiş bir sınıf (örneğin, a) arasında bulunan "bir" ilişki türü anlamına gelmez `Mammal` `Animal` . Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Daha fazla türetme engelleniyor  

Bir sınıf, kendisini veya üyeyi olarak bildirerek, diğer sınıfların kendisinden veya üyelerinden birinden devralmasını önleyebilir [`sealed`](../../language-reference/keywords/sealed.md) . Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Temel sınıf üyelerinin türetilmiş sınıf gizlemesi  

Türetilmiş bir sınıf, aynı ada ve imzaya sahip üyeleri bildirerek, temel sınıf üyelerini gizleyebilir. [`new`](../../language-reference/keywords/new-modifier.md)Değiştirici, üyenin temel üyenin bir geçersiz kılma olması amaçlanmadığını açıkça belirtmek için kullanılabilir. Kullanılması [`new`](../../language-reference/keywords/new-modifier.md) gerekli değildir, ancak kullanılmazsa bir derleyici uyarısı oluşturulacaktır [`new`](../../language-reference/keywords/new-modifier.md) . Daha fazla bilgi için bkz. geçersiz kılma ve [Yeni anahtar sözcüklerle sürüm oluşturma](./versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [sınıfı](../../language-reference/keywords/class.md)
