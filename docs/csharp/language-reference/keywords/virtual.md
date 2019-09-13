---
title: sanal C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 586e50818fc8ceaad5ca1925c0636b31015d81d4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925367"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)

`virtual` Anahtar sözcüğü bir yöntemi, özelliği, Dizin Oluşturucuyu veya olay bildirimini değiştirmek ve bir türetilmiş sınıfta geçersiz kılınmasına izin vermek için kullanılır. Örneğin, bu yöntem onu devralan herhangi bir sınıf tarafından geçersiz kılınabilir:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Bir sanal üyenin uygulanması türetilmiş bir sınıftaki [geçersiz kılan bir üye](override.md) tarafından değiştirilebilir. `virtual` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için, bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Açıklamalar

Bir sanal yöntem çağrıldığında, nesnenin çalışma zamanı türü geçersiz kılan üye için denetlenir. Türetilmiş bir sınıf üye tarafından geçersiz kılınmamışsa, en çok türetilen sınıftaki geçersiz kılan üye çağrılır, bu, özgün üye olabilir.

Varsayılan olarak, metotlar sanal değildir. Sanal olmayan bir yöntemi geçersiz kılamazsınız.

`virtual` Değiştirici `static`, ,`abstract`, veya`override` değiştiriciyle kullanılamaz. `private` Aşağıdaki örnek bir sanal özelliği gösterir:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Bildirim ve çağırma sözdiziminde farklılıklar dışında, sanal Özellikler soyut yöntemler gibi davranır.

- `virtual` Değiştirici statik bir özellik üzerinde kullanılması hatadır.

- `override` Değiştirici kullanan bir özellik bildirimi eklenerek, türetilmiş bir sınıfta sanal devralınmış bir özellik geçersiz kılınabilir.

## <a name="example"></a>Örnek

Bu örnekte `Shape` , sınıfı iki `y`koordinat `x`, ve `Area()` sanal yöntemi içerir. `Circle`, ,`Cylinder`Ve gibifarklışekil`Shape` sınıfları ve yüzey alanı her bir şekil için hesaplanır. `Sphere` Türetilmiş her sınıf kendi geçersiz kılma uygulamasına `Area()`sahiptir.

Devralınan sınıfların `Circle`, `Sphere`ve `Cylinder` tümünün, aşağıdaki bildirimde gösterildiği gibi, temel sınıfı başlatacak olan oluşturuculara sahip olduğuna dikkat edin.

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
