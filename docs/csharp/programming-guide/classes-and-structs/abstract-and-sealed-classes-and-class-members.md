---
title: Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715003"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri (C# Programlama Kılavuzu)
[Soyut](../../language-reference/keywords/abstract.md) anahtar kelime, eksik olan ve türemiş bir sınıfta uygulanması gereken sınıflar ve [sınıf](../../language-reference/keywords/class.md) üyeleri oluşturmanıza olanak tanır.  
  
 [Mühürlü](../../language-reference/keywords/sealed.md) anahtar kelime, daha önce [sanal](../../language-reference/keywords/virtual.md)olarak işaretlenmiş bir sınıfın veya belirli sınıf üyelerinin devrinin engellenmesini sağlar.  
  
## <a name="abstract-classes-and-class-members"></a>Soyut Sınıflar ve Sınıf Üyeleri  
 Sınıflar, anahtar sözcüğü `abstract` sınıf tanımının önüne koyarak soyut olarak bildirilebilir. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Soyut bir sınıf anında alınamaz. Soyut sınıfın amacı, birden çok türetilmiş sınıfın paylaşabileceği bir taban sınıfın ortak bir tanımını sağlamaktır. Örneğin, bir sınıf kitaplığı, işlevlerinin çoğu için parametre olarak kullanılan soyut bir sınıf tanımlayabilir ve türemiş bir sınıf oluşturarak sınıfın kendi uygulamasını sağlamak için bu kitaplığı kullanan programcılar gerektirir.  
  
 Soyut sınıflar soyut yöntemleri de tanımlayabilir. Bu yöntemin dönüş türünden `abstract` önce anahtar kelime ekleyerek gerçekleştirilir. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Soyut yöntemlerin uygulanması yoktur, bu nedenle yöntem tanımı normal bir yöntem bloğu yerine bir yarı kolon tarafından izlenir. Soyut sınıfın türemiş sınıfları tüm soyut yöntemleri uygulamalıdır. Soyut bir sınıf bir temel sınıftan sanal bir yöntem devraldığında, soyut sınıf soyut bir yöntemle sanal yöntemi geçersiz kılabilir. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Bir `virtual` yöntem bildirilirse, `abstract`soyut sınıftan devralan herhangi bir sınıf için hala sanaldır. Soyut bir yöntem devralan bir sınıf yöntemin özgün uygulamasına `DoWork` erişemez—önceki `DoWork` örnekte, F sınıfında D sınıfı çağrı yapamaz. Bu şekilde, soyut bir sınıf türemiş sınıfları sanal yöntemler için yeni yöntem uygulamaları sağlamaya zorlayabilir.  
  
## <a name="sealed-classes-and-class-members"></a>Mühürlü Sınıflar ve Sınıf Üyeleri  
 Sınıflar, anahtar kelime `sealed` sınıf tanımının önüne konularak [mühürlenmiş](../../language-reference/keywords/sealed.md) olarak bildirilebilir. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Mühürlü bir sınıf taban sınıf olarak kullanılamaz. Bu nedenle, aynı zamanda soyut bir sınıf olamaz. Mühürlü sınıflar türeciliği önler. Hiçbir zaman taban sınıf olarak kullanılamayacağından, bazı çalışma zamanı optimizasyonları mühürlü sınıf üyelerini biraz daha hızlı çağırabilir.  
  
 Taban sınıfın sanal bir üyesini geçersiz kılan türemiş bir sınıftaki yöntem, dizinleyici, özellik veya olay, bu üyenin mühürlü olduğunu bildirebilir. Bu, başka türemiş herhangi bir sınıf için üyenin sanal yönünü inkâr eder. Bu, `sealed` anahtar sözcüğü sınıf üye bildiriminde [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcüğünün önüne koyarak gerçekleştirilir. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Devralma](./inheritance.md)
- [Yöntemler](./methods.md)
- [Alanlar](./fields.md)
- [Soyut özellikleri tanımlama](./how-to-define-abstract-properties.md)
