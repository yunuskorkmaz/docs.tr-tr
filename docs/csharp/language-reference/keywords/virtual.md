---
title: sanal - C# Referans
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173464"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)

Anahtar `virtual` kelime, bir yöntemi, özelliği, dizinleyiciyi veya olay bildirimini değiştirmek ve türetilmiş bir sınıfta geçersiz kılınmasını sağlamak için kullanılır. Örneğin, bu yöntem, onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:

```csharp
public virtual double Area()
{
    return x * y;
}
```

Sanal bir üyenin uygulanması, türetilmiş bir [sınıftaki geçersiz bir üye](override.md) tarafından değiştirilebilir. Anahtar kelimenin `virtual` nasıl kullanılacağı hakkında daha fazla bilgi için, [Geçersiz Kılma ve Yeni Anahtar Kelimelerle Sürümleme ve](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) Geçersiz Kılma ve Yeni Anahtar Kelimeleri Ne Zaman [Kullanılacağını Bilmek](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)'e bakın.

## <a name="remarks"></a>Açıklamalar

Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz bir üye için denetlenir. En çok türetilmiş sınıftaki geçersiz olan üye, türetilmiş sınıf üyeyi geçersiz kılmamışsa, özgün üye olabilecek çağrılır.

Varsayılan olarak, yöntemler sanal değildir. Sanal olmayan bir yöntemi geçersiz kılamazsınız.

`virtual` Değiştiriciyi `static`, `abstract`, `private`veya `override` değiştiriciler ile kullanamazsınız. Aşağıdaki örnekte sanal bir özellik gösterilmektedir:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Sanal özellikler, bildirim ve çağırma sözdiziminde olan farklılıklar dışında sanal yöntemler gibi olur.

- `virtual` Statik bir özellik üzerinde değiştirici kullanmak bir hatadır.

- Sanal devralınan özellik, `override` değiştiriciyi kullanan bir özellik bildirimi ekleyerek türetilmiş bir sınıfta geçersiz kılınabilir.

## <a name="example"></a>Örnek

Bu örnekte, `Shape` sınıf iki koordinat `x` `y`, ve `Area()` sanal yöntem içerir. Sınıf , , `Circle` `Cylinder`ve `Sphere` devralma `Shape` gibi farklı şekil sınıfları ve yüzey alanı her şekil için hesaplanır. Her türetilmiş sınıfın kendi `Area()`geçersiz kılma uygulaması vardır.

Aşağıdaki bildirimde gösterildiği `Circle` `Sphere`gibi, `Cylinder` devralınan sınıfların ve tüm bunların temel sınıfı açan yapıcılar kullandığına dikkat edin.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Aşağıdaki program, `Area()` yöntemle ilişkili nesneye göre yöntemin uygun uygulamasını çağırarak her şekil için uygun alanı hesaplar ve görüntüler.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
- [Soyut](abstract.md)
- [Geçersiz kılma](override.md)
- [yeni (değiştirici)](new-modifier.md)
