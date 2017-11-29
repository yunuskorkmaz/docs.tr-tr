---
title: "abstract (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 785c23294abdbfa0684560a38fbd0279200a7d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-c-reference"></a>abstract (C# Başvurusu)
`abstract` Değiştiricisi değiştirilen bir şey yok veya eksik bir uygulaması olduğunu gösterir. Soyut değiştiricisi sınıfları, yöntemleri, özellikleri, dizin oluşturucular ve olayları ile kullanılabilir. Kullanım `abstract` bir sınıfı diğer sınıfların temel sınıf yalnızca olması amaçlanmıştır belirtmek için bir sınıf bildirimindeki değiştiricisi. Özet olarak işaretlenmiş ya da bir Özet sınıfta dahil üyeleri soyut sınıftan türeyen sınıflar tarafından uygulanmalıdır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıf `Square` uygulaması sağlamalısınız `Area` öğesinden türetilen çünkü `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 Soyut sınıflar, aşağıdaki özelliklere sahiptir:  
  
-   Bir Özet sınıfın örneği oluşturulamıyor.  
  
-   Bir Özet Sınıf soyut yöntemler ve erişimciler içerebilir.  
  
-   Bir Özet sınıf değiştirmek mümkün değil [korumalı](../../../csharp/language-reference/keywords/sealed.md) değiştiricisi iki modifers ters anlamları olduğundan. `sealed` Değiştiricisi devralınan öğesinden bir sınıf engeller ve `abstract` değiştiricisi devralınan için bir sınıf gerektirir.  
  
-   Bir özet sınıftan türetilen soyut olmayan sınıfı devralınan tüm soyut yöntemler ve erişimciler gerçek uygulamaları içermelidir.  
  
 Kullanım `abstract` değiştirici yöntemi veya özelliği uygulama içermediğini belirtmek için yöntemi veya özelliği bir bildirimi.  
  
 Soyut yöntemler aşağıdaki özelliklere sahiptir:  
  
-   Soyut bir yöntem örtük olarak sanal bir yöntemdir.  
  
-   Özet yöntem bildirimleri yalnızca soyut sınıflarda izin verilir.  
  
-   Bir Özet yöntem bildirimi gerçek uygulaması sağladığından, hiçbir yöntem gövdesi yoktur; yöntem bildirimi yalnızca noktalı virgül ile sona erer ve imza izleyen hiçbir süslü ayraçlar ({}) vardır. Örneğin:  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     Uygulama bir geçersiz kılma yöntemi tarafından sağlanan[geçersiz kılma](../../../csharp/language-reference/keywords/override.md), soyut olmayan sınıfı üyesi olduğu.  
  
-   Kullanmak için bir hata olduğunu [statik](../../../csharp/language-reference/keywords/static.md) veya [sanal](../../../csharp/language-reference/keywords/virtual.md) değiştiricileri bir Özet yöntem bildirimi.  
  
 Soyut özellikler bildirim ve çağırma söz dizimi farklılıkları dışında soyut yöntemler gibi davranır.  
  
-   Kullanmak için bir hata olduğunu `abstract` bir statik özelliğe değiştiricisi.  
  
-   Soyut devralınmış bir özellik türetilen bir sınıfta kullanan bir özellik bildirimi dahil olmak üzere geçersiz kılınabilir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi.  
  
 Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Soyut bir sınıf uygulama tüm arabirim üyeleri için sağlamanız gerekir.  
  
 Bir arabirimini uygulayan bir Özet Sınıf soyut yöntemler üzerine arabirim yöntemleri eşleyebilir. Örneğin:  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıf `DerivedClass` bir özet sınıftan türetilen `BaseClass`. Soyut bir yöntem soyut sınıf içeren `AbstractMethod`ve iki soyut özellikleri `X` ve `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 Önceki örnekte, böyle bir deyimi kullanarak soyut sınıf örneği çalışırsanız:  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 Derleyici 'BaseClass' bir Özet sınıfın örneği oluşturulamıyor bildiren bir hata alırsınız.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [sanal](../../../csharp/language-reference/keywords/virtual.md)  
 [geçersiz kılma](../../../csharp/language-reference/keywords/override.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)
