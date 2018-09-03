---
title: virtual (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 384cc442e51ec96cafe9b44ef945bb913b0e65f6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484047"
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)
`virtual` Anahtar sözcüğü, bir yöntemi, özelliği, dizin oluşturucu veya olay bildirimini değiştirmek ve türetilen bir sınıfta geçersiz kılınması için izin vermek için kullanılır. Örneğin, bu yöntem devraldığı herhangi bir sınıf tarafından geçersiz kılınabilir:  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Uygulamasını bir sanal üye tarafından değiştirilebilen bir [geçersiz kılan üye](../../../csharp/language-reference/keywords/override.md) türetilen bir sınıfta. Nasıl kullanılacağı hakkında daha fazla bilgi için `virtual` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [bilerek, geçersiz kılma kullanın ve yeni anahtar sözcüklerle](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Sanal bir yöntem çağrıldığında, nesnenin çalışma zamanı türü için geçersiz kılan bir üye denetlenir. Türetilmiş sınıf üyesi kıldıysa, özgün üyesi olabilir. en çok türetilen bir sınıfta geçersiz kılan üye çağrılır.  
  
 Varsayılan olarak, sanal olmayan yöntemlerdir. Sanal olmayan bir yöntemi geçersiz kılınamıyor.  
  
 Kullanamazsınız `virtual` değiştiriciyle `static`, `abstract`, `private`, veya `override` değiştiriciler. Aşağıdaki örnek, sanal bir özellik gösterilmiştir:  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Sanal özellikler, bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.  
  
-   Kullanılacak bir hata olduğunu `virtual` değiştirici statik bir özellik.  
  
-   Sanal bir devralınan özelliği kullanan bir özellik bildirimi dahil olmak üzere türetilen bir sınıfta kılınabilir `override` değiştiricisi.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Shape` sınıfı içeren iki koordinat `x`, `y`ve `Area()` sanal yöntem. Farklı şekil sınıflar gibi `Circle`, `Cylinder`, ve `Sphere` devral `Shape` sınıfı ve yüzey her şekil için hesaplanır. Her bir türetilmiş sınıf kendi geçersiz kılma uygulaması olan `Area()`.  
  
 Dikkat devralınan sınıflar `Circle`, `Sphere`, ve `Cylinder` tüm taban sınıf başlatma oluşturucular aşağıdaki bildirimde gösterildiği gibi kullanın.  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Aşağıdaki program hesaplar ve her bir şekil için uygun alan uygun uygulama çağırarak görüntüler `Area()` yöntemiyle ilişkili nesne göre yöntemi.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [abstract](../../../csharp/language-reference/keywords/abstract.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [new](../../../csharp/language-reference/keywords/new.md)
