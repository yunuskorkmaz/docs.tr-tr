---
title: virtual (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dce3333646bca6f558e3760849b6cffdb34a6c0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-c-reference"></a>virtual (C# Başvurusu)
`virtual` Anahtar sözcüğü bir yöntemi, özelliği, dizin oluşturucu veya olay bildiriminin değiştirebilir ve türetilen bir sınıfta geçersiz kılınmak üzere izin için kullanılır. Örneğin, bu yöntem, devralınan herhangi bir sınıf tarafından geçersiz kılınabilir:  
  
```  
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
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Aşağıdaki programı hesaplar ve uygun uygulanması harekete geçirerek her şekil için uygun alanı görüntüler `Area()` yöntemiyle ilişkili nesne göre yöntemi.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Özet](../../../csharp/language-reference/keywords/abstract.md)  
 [geçersiz kılma](../../../csharp/language-reference/keywords/override.md)  
 [Yeni](../../../csharp/language-reference/keywords/new.md)
