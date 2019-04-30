---
title: Sanal - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: eede3359b195661ff89a387e9b226bc970c27942
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660378"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)

`virtual` Anahtar sözcüğü, bir yöntemi, özelliği, dizin oluşturucu veya olay bildirimini değiştirmek ve türetilen bir sınıfta geçersiz kılınması için izin vermek için kullanılır. Örneğin, bu yöntem devraldığı herhangi bir sınıf tarafından geçersiz kılınabilir:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Uygulamasını bir sanal üye tarafından değiştirilebilen bir [geçersiz kılan üye](override.md) türetilen bir sınıfta. Nasıl kullanılacağı hakkında daha fazla bilgi için `virtual` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [bilerek, geçersiz kılma kullanın ve yeni anahtar sözcüklerle](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Açıklamalar

Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü için geçersiz kılan bir üye denetlenir. Türetilmiş sınıf üyesi kıldıysa, özgün üyesi olabilir. en çok türetilen bir sınıfta geçersiz kılan üye çağrılır.

Varsayılan olarak, sanal olmayan yöntemlerdir. Sanal olmayan bir yöntemi geçersiz kılınamıyor.

Kullanamazsınız `virtual` değiştiriciyle `static`, `abstract`, `private`, veya `override` değiştiriciler. Aşağıdaki örnek, sanal bir özellik gösterilmiştir:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.

- Kullanılacak bir hata olduğunu `virtual` değiştirici statik bir özellik.

- Sanal bir devralınan özelliği kullanan bir özellik bildirimi dahil olmak üzere türetilen bir sınıfta kılınabilir `override` değiştiricisi.

## <a name="example"></a>Örnek

Bu örnekte, `Shape` sınıfı içeren iki koordinat `x`, `y`ve `Area()` sanal yöntem. Farklı şekil sınıflar gibi `Circle`, `Cylinder`, ve `Sphere` devral `Shape` sınıfı ve yüzey her şekil için hesaplanır. Her bir türetilmiş sınıf kendi geçersiz kılma uygulaması olan `Area()`.

Dikkat devralınan sınıflar `Circle`, `Sphere`, ve `Cylinder` tüm taban sınıf başlatma oluşturucular aşağıdaki bildirimde gösterildiği gibi kullanın.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Aşağıdaki program hesaplar ve her bir şekil için uygun alan uygun uygulama çağırarak görüntüler `Area()` yöntemiyle ilişkili nesne göre yöntemi.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Değiştiriciler](modifiers.md)
- [C# Anahtar Sözcükleri](index.md)
- [Çok biçimlilik](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [new](new.md)