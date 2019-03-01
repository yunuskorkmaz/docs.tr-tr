---
title: Soyut ve korumalı sınıflar ve sınıf üyeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: fc3e29ad606cf8a60318a320e8ebc65b0d7f6e48
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965260"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)
[Soyut](../../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü sınıflar oluşturmanıza olanak sağlar ve [sınıfı](../../../csharp/language-reference/keywords/class.md) , eksik olan ve türetilen bir sınıfta uygulanması gereken üyeleri.  
  
 [Korumalı](../../../csharp/language-reference/keywords/sealed.md) anahtar sözcüğü bir sınıf ya da önceden işaretlenmiş belirli sınıf üyelerinin devralınmasını önlemenizi sağlar sağlayan [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Soyut sınıflar ve sınıf üyeleri  
 Sınıfları bildirilebilir soyut olarak anahtar sözcüğü yerleştirilerek `abstract` sınıf tanımından önce. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Bir soyut sınıfı oluşturulamıyor. Amacı bir soyut sınıfı, birden çok türetilmiş sınıflar paylaşabileceğiniz bir taban sınıfın ortak bir tanımını sağlamaktır. Örneğin, bir sınıf kitaplığı işlevlerinden birçoğuna bir parametre olarak kullanılan bir soyut sınıfını tanımlayabilir ve programcıların bir türetilmiş sınıf oluşturarak sınıf kendi uygulamasını sağlamak üzere bu kitaplığı kullanarak gerektirir.  
  
 Soyut sınıfları ayrıca soyut yöntemlerini de tanımlayabilir. Bu anahtar sözcüğü eklenerek elde edilir `abstract` yöntemin dönüş türünden önce. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Yöntem tanımını ve ardından normal yöntem bloğu yerine bir noktalı virgül şekilde soyut yöntemler, uygulaması bulunmuyor. Soyut sınıfının türetilmiş sınıfları tüm soyut yöntemlerini uygulamalıdır. Bir Özet sınıf bir taban sınıftan sanal bir yöntemi devraldığında, soyut sınıf sanal yöntemi soyut bir yöntemle geçersiz kılabilirsiniz. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Varsa bir `virtual` yöntemi bildirilmiş `abstract`, hala soyut sınıfından devralan herhangi bir sınıf için sanal. Bir soyut yönteminden devralan bir sınıf, yöntemin asıl uygulamasına erişemez; önceki örnekte, `DoWork` F çağıramaz sınıfında `DoWork` sınıfı d Bu yolla bir soyut sınıfı türetilen sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamak için zorlayabilirsiniz.  
  
## <a name="sealed-classes-and-class-members"></a>Korumalı sınıflar ve sınıf üyeleri  
 Sınıflar olarak bildirilebilir [korumalı](../../../csharp/language-reference/keywords/sealed.md) anahtar sözcüğü yerleştirilerek `sealed` sınıf tanımından önce. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Korumalı sınıf bir taban sınıfı olarak kullanılamaz. Bu nedenle, bir soyut sınıfı da olamaz. Korumalı sınıflar türetmeyi önler. Temel sınıf olarak hiçbir zaman kullanılabilir olduğundan, bazı çalışma zamanı iyileştirmeleri korumalı sınıf üyelerinin biraz daha hızlı arama yapabilirsiniz.  
  
 Yöntemi, dizin oluşturucu, özellik veya olay, temel sınıf sanal bir üyesinin geçersiz kılan türetilmiş bir sınıfta o üyeyi korumalı olarak bildirebilir. Bu daha fazla türetilmiş herhangi bir sınıf üyesinin sanal yönünü olumsuz duruma getirir. Konarak elde edilir `sealed` anahtar sözcüğünün önüne [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) sınıf üyesi bildiriminde anahtar sözcüğü. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Nasıl yapılır: Soyut özellikleri tanımlama](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
