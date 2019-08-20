---
title: Soyut ve korumalı sınıflar ve sınıf üyeleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 1c98e2979ee96d4bcc885b8cc797eaac28c8d2ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597298"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)
[Abstract](../../language-reference/keywords/abstract.md) anahtar sözcüğü, tamamlanmamış ve türetilmiş bir sınıfta uygulanması gereken sınıflar ve [sınıf](../../language-reference/keywords/class.md) üyeleri oluşturmanızı sağlar.  
  
 [Sealed](../../language-reference/keywords/sealed.md) anahtar sözcüğü, bir sınıfın devralınmasını veya daha önce [sanal](../../language-reference/keywords/virtual.md)olarak işaretlenmiş belirli sınıf üyelerini engellemenizi sağlar.  
  
## <a name="abstract-classes-and-class-members"></a>Soyut sınıflar ve sınıf üyeleri  
 Sınıflar, sınıf tanımından önce anahtar sözcüğü `abstract` yerleştirilerek soyut olarak bildirilemez. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Soyut bir sınıf örneği oluşturulamıyor. Soyut bir sınıfın amacı, birden fazla türetilmiş sınıfın paylaşabileceği bir temel sınıfın ortak bir tanımını sağlamaktır. Örneğin, bir sınıf kitaplığı, işlevlerinin çoğuna parametre olarak kullanılan bir soyut sınıfı tanımlayabilir ve bir türetilmiş sınıf oluşturarak bu kitaplığı kullanan programcıların, sınıfının kendi uygulamasını sağlamasını gerektirebilir.  
  
 Soyut sınıflar, Soyut yöntemler de tanımlayabilir. Bu, yönteminin dönüş türünden önce anahtar `abstract` sözcüğü eklenerek yapılır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Soyut yöntemlerin hiçbir uygulamaya sahip olmadığı için, yöntem tanımının normal yöntem bloğu yerine noktalı virgül gelmelidir. Soyut sınıfın türetilmiş sınıfları tüm soyut yöntemleri uygulamalıdır. Bir soyut sınıf bir temel sınıftan sanal bir yöntemi devralıyorsa, soyut sınıf, soyut bir yöntemle sanal yöntemi geçersiz kılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Bir `virtual` Yöntem bildirilirse `abstract`, soyut sınıftan devralan herhangi bir sınıfta hala sanal olur. Soyut bir yöntemi devralan sınıf, yöntemin orijinal uygulamasına erişemez — önceki örnekte, F sınıfı üzerinde, `DoWork` D sınıfı üzerinde çağrılamaz. `DoWork` Bu şekilde, soyut bir sınıf, türetilmiş sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamaya zorlayabilir.  
  
## <a name="sealed-classes-and-class-members"></a>Korumalı sınıflar ve sınıf üyeleri  
 Sınıflar, sınıf tanımından önce [](../../language-reference/keywords/sealed.md) anahtar sözcüğü `sealed` yerleştirilerek Sealed olarak bildirilebilecek. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Sealed bir sınıf temel sınıf olarak kullanılamaz. Bu nedenle, bir soyut sınıf de olamaz. Sealed sınıflar türetmeye engel. Bunlar hiçbir zaman temel sınıf olarak kullanılabileceğinden, bazı çalışma zamanı iyileştirmeleri sealed sınıf üyelerinin çağrılmasını biraz daha hızlı hale getirir.  
  
 Temel sınıfın bir sanal üyesini geçersiz kılan türetilmiş bir sınıfta bir yöntem, Dizin Oluşturucu, özellik veya olay bu üyeyi korumalı olarak bildirebilir. Bu, daha fazla türetilmiş sınıf için üyenin sanal yönünü geçersiz kılar. Bu, `sealed` anahtar sözcüğü, sınıf üye bildirimindeki [override](../../language-reference/keywords/override.md) anahtar sözcüğünden önce yerleştirilerek gerçekleştirilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Devralma](./inheritance.md)
- [Yöntemler](./methods.md)
- [Alanlar](./fields.md)
- [Nasıl yapılır: Soyut özellikleri tanımla](./how-to-define-abstract-properties.md)
