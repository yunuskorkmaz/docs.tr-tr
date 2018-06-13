---
title: virtual (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 5a188e9a7cbb7a1c497d577039c2b2578eaa7526
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172652"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)
`virtual` Anahtar sözcüğü bir yöntemi, özelliği, dizin oluşturucu veya olay bildiriminin değiştirebilir ve türetilen bir sınıfta geçersiz kılınmak üzere izin için kullanılır. Örneğin, bu yöntem, devralınan herhangi bir sınıf tarafından geçersiz kılınabilir:  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Uygulaması sanal bir üyesi tarafından değiştirilebilir bir [geçersiz kılma üye](../../../csharp/language-reference/keywords/override.md) türetilmiş bir sınıf içinde. Nasıl kullanılacağı hakkında daha fazla bilgi için `virtual` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [kullanmak geçersiz kılma ve yeni anahtar sözcüklerin için bilerek olduğunda](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü için geçersiz kılma bir üye denetlenir. Türetilmiş bir sınıf üyesi kıldıysa, özgün üye olabilir en çok türetilen sınıfı geçersiz kılan üye denir.  
  
 Varsayılan olarak, sanal olmayan yöntemleridir. Sanal olmayan bir yöntem geçersiz kılamaz.  
  
 Kullanamazsınız `virtual` değiştiricisi ile `static`, `abstract`, `private`, veya `override` değiştiricileri. Aşağıdaki örnek, bir sanal özelliği gösterir:  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Sanal özellikler bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.  
  
-   Kullanmak için bir hata olduğunu `virtual` bir statik özelliğe değiştiricisi.  
  
-   Sanal bir devralınan özelliği kullanan bir özellik bildirimi dahil ederek türetilen bir sınıfta kılınabilir `override` değiştiricisi.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Shape` sınıfı içeren iki koordinat `x`, `y`ve `Area()` sanal yöntemi. Farklı şekil sınıfları gibi `Circle`, `Cylinder`, ve `Sphere` devral `Shape` sınıfı ve yüzey alanını her şekil için hesaplanır. Her türetilmiş bir sınıf, geçersiz kılma uyarlamasını kendi sahip `Area()`.  
  
 Dikkat devralınan sınıfları `Circle`, `Sphere`, ve `Cylinder` tüm taban sınıf başlatmak oluşturucular aşağıdaki bildiriminde gösterildiği gibi kullanın.  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Aşağıdaki programı hesaplar ve uygun uygulanması harekete geçirerek her şekil için uygun alanı görüntüler `Area()` yöntemiyle ilişkili nesne göre yöntemi.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [new](../../../csharp/language-reference/keywords/new.md)
