---
title: sanal C# başvuru
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 47b77792fd3a2b2700ec0734851fdec534361596
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712877"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)

`virtual` anahtar sözcüğü, bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınabilmesi için kullanılır. Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir. `virtual` anahtar sözcüğünü kullanma hakkında daha fazla bilgi için bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Açıklamalar

Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir. Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.

Varsayılan olarak, metotlar sanal değildir. Sanal olmayan bir yöntemi geçersiz kılamazsınız.

`virtual` değiştiricisini `static`, `abstract`, `private`veya `override` değiştiriciyle kullanamazsınız. Aşağıdaki örnek bir sanal özelliği gösterir:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında sanal yöntemler gibi davranır.

- Statik bir özellik üzerinde `virtual` değiştiricisinin kullanılması hatadır.

- Bir sanal devralınmış özellik, `override` değiştiricisini kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta geçersiz kılınabilir.

## <a name="example"></a>Örnek

Bu örnekte, `Shape` sınıfı iki koordinat `x`, `y`ve `Area()` sanal yöntemi içerir. `Circle`, `Cylinder`ve `Sphere` gibi farklı şekil sınıfları `Shape` sınıfını miras alır ve yüzey alanı her bir şekil için hesaplanır. Her türetilmiş sınıfın `Area()`geçersiz kılma uygulamasına sahiptir.

Devralınan sınıfların `Circle`, `Sphere`ve `Cylinder`, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Aşağıdaki program, yöntemiyle ilişkili nesneye göre `Area()` yönteminin uygun uygulamasını çağırarak her bir şekil için uygun alanı hesaplar ve görüntüler.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [Yeni (değiştirici)](new-modifier.md)
