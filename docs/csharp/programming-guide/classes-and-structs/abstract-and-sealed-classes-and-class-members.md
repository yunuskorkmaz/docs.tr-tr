---
title: "Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dac7570c018bd577faac4540e4d800cc11143578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)
[Soyut](../../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü sınıfları oluşturmanıza olanak sağlar ve [sınıfı](../../../csharp/language-reference/keywords/class.md) tamamlanmamış ve türetilen bir sınıfta uygulanmalı üyeleri.  
  
 [Korumalı](../../../csharp/language-reference/keywords/sealed.md) anahtar sözcüğü bir sınıf ya da daha önce işaretlenen belirli sınıfı üyeleri devralma önlemek etkinleştirir [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Soyut sınıflar ve sınıf üyeleri  
 Sınıfları bildirilebilir soyut olarak anahtar sözcüğü koyarak `abstract` sınıf tanımını önce. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Bir Özet sınıfın örneği oluşturulamıyor. Bir Özet sınıf amacı bir taban sınıfın birden çok türetilen sınıflar paylaşabilirsiniz ortak bir tanımı sağlamaktır. Örneğin, bir sınıf kitaplığı birçok işlevlerini parametre olarak kullanılan soyut bir sınıf tanımlama ve türetilmiş bir sınıf oluşturarak, kendi uygulama sınıfının sağlamak için bu kitaplığı kullanarak programcıları gerektirir.  
  
 Soyut sınıfların soyut yöntemler de tanımlayabilir. Bu anahtar sözcüğü ekleyerek gerçekleştirilir `abstract` önce yönteminin dönüş türü. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Soyut yöntemler hiçbir uygulama sahip, bu nedenle yöntem tanımı normal yöntem bloğu yerine noktalı izlenir. Soyut sınıftan türetilen sınıflar tüm soyut yöntemler uygulamalıdır. Soyut bir sınıf sanal bir yöntem bir taban sınıftan, soyut sınıf ile soyut bir yöntem sanal yöntemi geçersiz kılabilirsiniz. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Varsa bir `virtual` yöntemi bildirilen `abstract`, soyut sınıfından devralan herhangi bir sınıf için hala sanal. Soyut bir yöntem devralan bir sınıf yöntemi'nın özgün uygulaması erişemiyor — önceki örnekte, `DoWork` F çağıramaz sınıfındaki `DoWork` sınıfı D. üzerinde Bu şekilde, bir Özet sınıf sanal yöntemler için yeni yöntemi uygulamaları sağlamak için türetilen sınıflar zorlayabilirsiniz.  
  
## <a name="sealed-classes-and-class-members"></a>Korumalı sınıflar ve sınıf üyeleri  
 Sınıflar olarak bildirilebilir [korumalı](../../../csharp/language-reference/keywords/sealed.md) anahtar sözcüğü koyarak `sealed` sınıf tanımını önce. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Korumalı bir sınıfın temel sınıf olarak kullanılamaz. Bu nedenle, bu da bir Özet sınıf olamaz. Sealed sınıfları türetme engeller. Bir temel sınıf olarak hiçbir zaman kullanılabilir olduğundan, bazı çalışma zamanı iyileştirmeleri biraz daha hızlı arama korumalı sınıf üyeleri yapabilirsiniz.  
  
 Yöntemi, dizin oluşturucu, özelliği veya olayda sanal temel sınıf üyesi geçersiz kılma türetilmiş bir sınıf, üye korumalı olarak bildirebilirsiniz. Bu üye için daha fazla türetilmiş bir sınıf sanal yönünü üzerindeki geçersiz kılar. Bu koyarak gerçekleştirilir `sealed` önce anahtar sözcüğü [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) sınıf üyesi bildirim anahtar sözcük. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Alanları](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Nasıl yapılır: soyut özellikleri tanımlama](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
