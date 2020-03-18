---
title: Polimorfizm - C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170175"
---
# <a name="polymorphism-c-programming-guide"></a>Çok Biçimlilik (C# Programlama Kılavuzu)

Polimorfizm genellikle kapsülleme ve kalıtım sonra, nesne yönelimli programlama üçüncü ayağı olarak adlandırılır. Polimorfizm Yunanca "çok şekilli" anlamına gelen bir kelimedir ve iki farklı yönü vardır:
  
- Çalışma zamanında, türemiş bir sınıfın nesneleri yöntem parametreleri ve koleksiyonlar veya diziler gibi yerlerde bir taban sınıfın nesneleri olarak kabul edilebilir. Bu çok biçimlilik oluştuğunda, nesnenin bildirilen türü artık çalışma zamanı türüyle aynı değildir.
- Temel sınıflar sanal [virtual](../../language-reference/keywords/virtual.md) *yöntemleri*tanımlayabilir ve uygulayabilir ve türetilmiş sınıflar bunları [geçersiz kılabilir,](../../language-reference/keywords/override.md) bu da kendi tanımlarını ve uygulamalarını sağladıkları anlamına gelir. Çalışma zamanında, istemci kodu yöntemi aradığında, CLR nesnenin çalışma zamanı türünü arar ve sanal yöntemin geçersiz kılınan çağrılarını çağırır. Kaynak kodunuzda, taban sınıfta bir yöntem çağırabilir ve yöntemin türetilmiş sınıf sürümünün yürütülmesine neden olabilirsiniz.

Sanal yöntemler, ilgili nesne gruplarıyla tek düze bir şekilde çalışmanızı sağlar. Örneğin, bir kullanıcının çizim yüzeyinde çeşitli şekiller oluşturmasına olanak tanıyan bir çizim uygulamanız olduğunu varsayalım. Derle diğiniz zaman, kullanıcının hangi belirli türde şekiller oluşturacağını bilemezsin. Ancak, uygulama oluşturulan şekillerin tüm çeşitli türlerini izlemek zorunda ve kullanıcı fare eylemleri yanıt olarak bunları güncelleştirmek zorundadır. Bu sorunu çözmek için çok biçimliliği iki temel adımda kullanabilirsiniz:

1. Her belirli şekil sınıfının ortak bir taban sınıftan türediği bir sınıf hiyerarşisi oluşturun.
1. Taban sınıf yöntemine tek bir çağrı yoluyla türemiş herhangi bir sınıftauygun yöntemi çağırmak için sanal bir yöntem kullanın.

İlk olarak, ,, `Shape`ve türemiş `Rectangle` `Circle`sınıflar `Triangle`, ve . `Shape` Sınıfa sanal `Draw`bir yöntem verin ve sınıfın temsil ettiği belirli şekli çizmek için her türetilmiş sınıfta geçersiz kılın. Bir `List<Shape>` nesne oluşturun `Circle`ve `Triangle`bir `Rectangle` , , ve ekleyin.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Çizim yüzeyini güncelleştirmek için, liste boyunca yinelemek için [foreach](../../language-reference/keywords/foreach-in.md) döngüsü `Shape` kullanın ve listedeki her nesnenin yöntemini `Draw` arayın. Listedeki her nesnenin beyan edilmiş `Shape`bir türü olsa da, çağrılacak çalışma zamanı türüdür (her türetilmiş sınıfta yöntemin geçersiz sürümü).

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

C#'da her tür polimorfiktir, çünkü kullanıcı tanımlı türler <xref:System.Object>de dahil olmak üzere tüm türler .  

## <a name="polymorphism-overview"></a>Polimorfizme genel bakış

### <a name="virtual-members"></a>Sanal üyeler

Türetilen bir sınıf bir taban sınıftan devraldığında, taban sınıfın tüm yöntemlerini, alanlarını, özelliklerini ve olaylarını kazanır. Türemiş sınıfın tasarımcısı sanal yöntemlerin davranışı için farklı seçimler yapabilir:

- Türetilen sınıf, yeni davranış tanımlayarak taban sınıftaki sanal üyeleri geçersiz kılabilir.
- Türetilen sınıf, varolan davranışı koruyarak, ancak daha fazla türetilmiş sınıfın yöntemi geçersiz kılmasını sağlayarak en yakın taban sınıf yöntemini geçersiz kılmadan devralır.
- Türemiş sınıf, taban sınıf uygulamalarını gizleyen bu üyelerin yeni sanal olmayan uygulamalarını tanımlayabilir.

Türetilen bir sınıf, taban sınıf [üyesinin sanal](../../language-reference/keywords/virtual.md) veya [soyut](../../language-reference/keywords/abstract.md)olarak bildirilmiş olması durumunda taban sınıf üyesini geçersiz kılabilir. Türemiş üye, yöntemin sanal çağırmaya katılmak üzere tasarlandığını açıkça belirtmek için [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcük anahtar sözcüklerini kullanmalıdır. Aşağıdaki kod bir örnek sağlar:

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Alanlar sanal olamaz; yalnızca yöntemler, özellikler, olaylar ve dizinleyiciler sanal olabilir. Türetilmiş bir sınıf sanal bir üyeyi geçersiz kıldığında, bu sınıfın bir örneğine taban sınıfın bir örneği olarak erişilse bile bu üye çağrılır. Aşağıdaki kod bir örnek sağlar:

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Sanal yöntemler ve özellikler, türemiş sınıfların bir yöntemin taban sınıf uygulamasını kullanmaya gerek kalmadan taban sınıfı genişletmesini sağlar. Daha fazla bilgi için, [Override ve Yeni Anahtar Kelimeler ile Sürümleme'ye](./versioning-with-the-override-and-new-keywords.md)bakın. Arabirim, uygulama türetilmiş sınıflara bırakılan bir yöntem veya yöntem kümesini tanımlamak için başka bir yol sağlar. Daha fazla bilgi için [Arabirimler'e](../interfaces/index.md)bakın.

### <a name="hide-base-class-members-with-new-members"></a>Yeni üyelerle taban sınıf üyelerini gizleme

Türemiş sınıfınızın taban sınıftaki bir üyeyle aynı ada sahip bir üyeye sahip olmasını istiyorsanız, taban sınıf üyesini gizlemek için [yeni](../../language-reference/keywords/new-modifier.md) anahtar sözcüğü kullanabilirsiniz. `new` Anahtar kelime, değiştirilen bir sınıf üyesinin dönüş türünden önce konur. Aşağıdaki kod bir örnek sağlar:

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Gizli taban sınıf üyeleri, türetilen sınıfın örneğini taban sınıfın bir örneğine atarak istemci kodundan erişilebilir. Örnek:

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Türetilen sınıfların sanal üyeleri geçersiz kılmasını önleme  

Sanal üyeler, sanal üye ile onu ilk bildiren sınıf arasında kaç sınıf beyan edildiğine bakılmaksızın sanal olarak kalır. Sınıf `A` `B` sanal bir üye bildirirse ve `A`sınıf, `C` sınıftan `B`türetilmiştir `C` ve sınıf, sanal üyeyi devralır ve sınıfın `B` o üye için geçersiz kılma ilan edip etmediğine bakılmaksızın onu geçersiz kılar. Aşağıdaki kod bir örnek sağlar:

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Türetilen bir [sınıf, geçersiz](../../language-reference/keywords/sealed.md)kılmayı mühürlü olarak beyan ederek sanal devralmayı durdurabilir. Devralmayı durdurmak `sealed` için anahtar `override` kelimenin sınıf üye bildiriminde anahtar kelimenin önüne konulması gerekir. Aşağıdaki kod bir örnek sağlar:

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

Önceki örnekte, yöntem `DoWork` artık türetilen herhangi bir `C`sınıf için sanal değil. Bu tür veya tür `C` `B` `A`döküm olsa bile, örnekleri için hala sanal. Mühürlü yöntemler, aşağıdaki örnekte görüldüğü `new` gibi, anahtar kelime kullanılarak türetilmiş sınıflar tarafından değiştirilebilir:

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

Bu durumda, `DoWork` tür `D` `D`bir değişken kullanılarak çağrılırsa, yeni `DoWork` denir. Türünde `C`bir değişken `B`, `A` veya bir örneğine `D`erişmek için `DoWork` kullanılırsa , bir çağrı sanal devralma kurallarına `DoWork` uyacak, sınıf `C`üzerinde uygulanmasına bu çağrıları yönlendirme .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Türemiş sınıflardan temel sınıf sanal üyelerine erişin

Bir yöntemin veya özelliğin yerini alan veya geçersiz kılınan türemiş bir `base` sınıf, anahtar sözcüğü kullanarak taban sınıftaki yönteme veya özelliğe erişebilir. Aşağıdaki kod bir örnek sağlar:

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

Daha fazla bilgi için [temele](../../language-reference/keywords/base.md)bakın.

> [!NOTE]
> Sanal üyelerin, bu `base` üyenin taban sınıf uygulamasını kendi uygulamalarında çağırmak için kullanmaları önerilir. Taban sınıf davranışının oluşmasına izin vermek, türemiş sınıfın türemiş sınıfa özgü davranışı uygulamaya odaklanmasını sağlar. Taban sınıf uygulaması çağrılmazsa, davranışlarını taban sınıfın davranışıyla uyumlu hale getirmek türemiş sınıfa kaçar.

## <a name="in-this-section"></a>Bu bölümde

- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](./versioning-with-the-override-and-new-keywords.md)
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](./knowing-when-to-use-override-and-new-keywords.md)
- [ToString yöntemini geçersiz kılma](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Devralma](./inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Yöntemler](./methods.md)
- [Olaylar](../events/index.md)
- [Özellikler](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Türler](../types/index.md)
