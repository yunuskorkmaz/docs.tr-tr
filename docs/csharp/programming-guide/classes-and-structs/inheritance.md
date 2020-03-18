---
title: Kalıtım - C# Programlama Kılavuzu
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 448b1695a4afc50f4afa20383e5fda280b9f12e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626665"
---
# <a name="inheritance-c-programming-guide"></a>Devralma (C# Programlama Kılavuzu)

Kalıtım, kapsülleme ve çok biçimlilik ile birlikte, nesne yönelimli programlamanın üç temel özelliğinden biridir. Devralma, diğer sınıflarda tanımlanan davranışı yeniden kullanan, genişleten ve değiştiren yeni sınıflar oluşturmanıza olanak tanır. Üyeleri devralınan *sınıfa taban sınıf,* bu üyeleri devralan sınıfa *ise türemiş sınıf*denir. Türetilen bir sınıfın yalnızca bir doğrudan taban sınıfı olabilir. Ancak, miras geçişli. 'den `ClassC` `ClassB`türetilmiş `ClassB` ve `ClassA`türetilmişse `ClassC` , `ClassB` `ClassA`beyan edilen üyeleri devralır ve .

> [!NOTE]
> Structs devralma desteklemez, ancak arabirimleri uygulayabilirsiniz. Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.

Kavramsal olarak, türemiş bir sınıf taban sınıfın bir uzmanlık olduğunu. Örneğin, bir taban sınıf `Animal`varsa, adlı `Mammal` bir türemiş sınıf ve adlı `Reptile`başka bir türetilmiş sınıf olabilir. A, `Mammal` `Animal`bir , `Reptile` ve `Animal`a , ama her türetilen sınıf taban sınıfın farklı uzmanlıkları temsil eder.

Arabirim bildirimleri üyeleri için varsayılan bir uygulama tanımlayabilir. Bu uygulamalar türetilmiş arabirimler ve bu arabirimleri uygulayan sınıflar tarafından devralınır. Varsayılan arabirim yöntemleri hakkında daha fazla bilgi için, dil başvuru bölümündeki [arabirimler](../../language-reference/keywords/interface.md) hakkındaki makaleye bakın.

Bir sınıfı başka bir sınıftan türeecek şekilde tanımladığınızda, türemiş sınıf, oluşturucuları ve sonlandırıcıları dışında taban sınıfın tüm üyelerini dolaylı olarak kazanır. Türemiş sınıf, kodu yeniden uygulamak zorunda kalmadan temel sınıfta yeniden kullanır. Türemiş sınıfa daha fazla üye ekleyebilirsiniz. Türemiş sınıf taban sınıfın işlevselliğini genişletir.

Aşağıdaki resimde, bazı `WorkItem` iş sürecinde bir çalışma öğesini temsil eden bir sınıf gösterilmektedir. Tüm sınıflar gibi, tüm <xref:System.Object?displayProperty=nameWithType> yöntemlerinden türetilmiştir ve ona miras kalır. `WorkItem`kendi beş üye ekler. Bu üyeler bir yapıcı içerir, çünkü kurucular kalıtsal değildir. Sınıf, `ChangeRequest` belirli `WorkItem` bir çalışma öğesi türünü devralır ve temsil eder. `ChangeRequest`ve bu üyelerden `WorkItem` <xref:System.Object>devraldığı üyelere iki üye daha ekler. Kendi yapıcıeklemek gerekir, ve aynı `originalItemID`zamanda ekler . Özellik, `originalItemID` örneğin `ChangeRequest` değişiklik isteğinin uygulandığı `WorkItem` orijinalle ilişkilendirilmesini sağlar.

![Sınıf kalıtımLarını gösteren diyagram](./media/inheritance/class-inheritance-diagram.png)

Aşağıdaki örnek, önceki resimde gösterilen sınıf ilişkilerinin C#ile nasıl ifade edilir olduğunu gösterir. Örnek, sanal `WorkItem` yöntemi <xref:System.Object.ToString%2A?displayProperty=nameWithType>nasıl geçersiz kdığını `ChangeRequest` ve sınıfın `WorkItem` yöntemin uygulanmasını nasıl devraldığı da gösterir. İlk blok sınıfları tanımlar:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Bir sonraki blok, taban ve türetilmiş sınıfların nasıl kullanılacağını gösterir:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Soyut ve sanal yöntemler

Bir taban sınıf bir yöntemi [`virtual`](../../language-reference/keywords/virtual.md), türemiş bir sınıf kendi uygulaması yla yöntem olabilir [`override`](../../language-reference/keywords/override.md) olarak bildirdiğinde. Bir taban sınıf bir üyeyi [`abstract`](../../language-reference/keywords/abstract.md), bu yöntemin bu sınıftan doğrudan devralınan soyut olmayan herhangi bir sınıfta geçersiz kılınması gerekir. Türemiş bir sınıf soyutsa, soyut üyeleri uygulamadan devralır. Soyut ve sanal üyeler, nesne yönelimli programlamanın ikinci birincil özelliği olan çok biçimliliğin temelidir. Daha fazla bilgi için [bkz.](./polymorphism.md)

## <a name="abstract-base-classes"></a>Soyut taban sınıfları

[Yeni](../../language-reference/operators/new-operator.md) işleci kullanarak doğrudan anlık durumu önlemek istiyorsanız, sınıfı [soyut](../../language-reference/keywords/abstract.md) olarak bildirebilirsiniz. Soyut bir sınıf yalnızca ondan yeni bir sınıf türetilmişse kullanılabilir. Soyut bir sınıf, kendilerini soyut olarak bildirilen bir veya daha fazla yöntem imzaları içerebilir. Bu imzalar parametreleri ve iade değerini belirtir, ancak uygulama (yöntem gövdesi) yoktur. Soyut bir sınıf soyut üyeleri içermemelidir; ancak, bir sınıf soyut bir üye içeriyorsa, sınıfın kendisi soyut olarak bildirilmelidir. Soyut olmayan türemiş sınıflar, soyut bir taban sınıftan soyut yöntemler için uygulama sağlamalıdır. Daha fazla bilgi için [Bkz. Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](abstract-and-sealed-classes-and-class-members.md)

## <a name="interfaces"></a>Arabirimler

*Arabirim,* bir üye kümesini tanımlayan bir başvuru türüdür. Bu arabirimi uygulayan tüm sınıflar ve structs bu üye kümesini uygulamalıdır. Arabirim, bu üyelerden herhangi biri veya tümü için varsayılan bir uygulama tanımlayabilir. Bir sınıf, yalnızca tek bir doğrudan taban sınıftan türebilse bile birden çok arabirim uygulayabilir.

Arabirimler, "bir ilişki" olması gerekmeyen sınıflar için belirli yetenekleri tanımlamak için kullanılır. Örneğin, <xref:System.IEquatable%601?displayProperty=nameWithType> arabirim, türdeki iki nesnenin eşdeğer olup olmadığını belirlemek için herhangi bir sınıf veya yapı tarafından uygulanabilir (ancak tür eşdeğerliği tanımlar). <xref:System.IEquatable%601>taban sınıf ile türemiş sınıf arasında var olan "bir" ilişki türünü ima `Mammal` etmez `Animal`(örneğin, a bir dir). Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.

## <a name="preventing-further-derivation"></a>Daha fazla türeme önleme  

Bir sınıf, kendisini veya üyeyi [`sealed`](../../language-reference/keywords/sealed.md). Daha fazla bilgi için [Bkz. Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri.](./abstract-and-sealed-classes-and-class-members.md)

## <a name="derived-class-hiding-of-base-class-members"></a>Taban sınıf üyelerinin türemiş sınıf gizleme  

Türemiş bir sınıf, aynı ada ve imzaya sahip üyeleri beyan ederek taban sınıf üyelerini gizleyebilir. Değiştirici, [`new`](../../language-reference/keywords/new-modifier.md) üyenin temel üyenin geçersiz kılınması amaçlanmadığını açıkça belirtmek için kullanılabilir. Kullanımı [`new`](../../language-reference/keywords/new-modifier.md) gerekli değildir, ancak kullanılmazsa [`new`](../../language-reference/keywords/new-modifier.md) derleyici uyarısı oluşturulur. Daha fazla bilgi için, [Override ve Yeni Anahtar Kelimeler ile Sürüm](./versioning-with-the-override-and-new-keywords.md) ve [Override ve Yeni Anahtar Kelimeler Ne Zaman Kullanılacağını Bilmek](./knowing-when-to-use-override-and-new-keywords.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Sınıfı](../../language-reference/keywords/class.md)
