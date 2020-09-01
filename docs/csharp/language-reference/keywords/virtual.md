---
description: Virtual-C# başvurusu
title: Virtual-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 67bdfcf27bb108ca85e94ba7fdce208e4cd83b80
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141731"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)

`virtual`Anahtar sözcüğü bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınmasına izin vermek için kullanılır. Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:

```csharp
public virtual double Area()
{
    return x * y;
}
```

Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir. Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `virtual` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Açıklamalar

Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir. Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.

Varsayılan olarak, metotlar sanal değildir. Sanal olmayan bir yöntemi geçersiz kılamazsınız.

Değiştirici,,, `virtual` `static` `abstract` `private` veya `override` değiştiriciyle kullanılamaz. Aşağıdaki örnek bir sanal özelliği gösterir:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında sanal yöntemler gibi davranır.

- `virtual`Değiştirici statik bir özellik üzerinde kullanılması hatadır.

- Değiştirici kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta sanal devralınmış bir özellik geçersiz kılınabilir `override` .

## <a name="example"></a>Örnek

Bu örnekte, `Shape` sınıfı iki koordinat, `x` `y` ve `Area()` sanal yöntemi içerir. ,, Ve gibi farklı şekil sınıfları `Circle` `Cylinder` `Sphere` `Shape` ve yüzey alanı her bir şekil için hesaplanır. Türetilmiş her sınıf kendi geçersiz kılma uygulamasına sahiptir `Area()` .

Devralınan sınıfların `Circle` , `Sphere` ve `Cylinder` tümünün, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Aşağıdaki program, yöntemiyle `Area()` ilişkili nesneye göre yönteminin uygun uygulamasını çağırarak her bir şekil için uygun alanı hesaplar ve görüntüler.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [Yeni (değiştirici)](new-modifier.md)
