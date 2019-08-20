---
title: Geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 58023498c499569eebb9a0506bea434d2669de45
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596002"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
Dil C# , farklı kitaplıklarda [temel](../../language-reference/keywords/base.md) ve türetilmiş sınıflar arasında sürüm oluşturmanın, geriye dönük uyumluluğu geliştirebilir ve bakımını yapabilmesi için tasarlanmıştır. Bu, örneğin, türetilmiş bir sınıftaki üye ile aynı ada sahip bir temel [sınıfta](../../language-reference/keywords/class.md) yeni bir üyenin giriş tarafından C# tamamen desteklendiği ve beklenmeyen davranışlara neden olmadığı anlamına gelir. Ayrıca, bir yöntemin devralınan bir yöntemi geçersiz kılmak için bir yöntemin açıkça veya bir yöntemin devralınmış bir adlandırılmış yöntemi gizleyen yeni bir yöntem olup olmadığı anlamına gelir.  
  
 ' C#De, türetilmiş sınıflar temel sınıf yöntemleriyle aynı ada sahip yöntemler içerebilir.  
  
- Temel sınıf yöntemi tanımlanmış bir [sanal](../../language-reference/keywords/virtual.md)olmalıdır.  
  
- Türetilmiş sınıftaki yöntemin önünde [Yeni](../../language-reference/keywords/new-modifier.md) veya [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcükleri yoksa, derleyici bir uyarı verecek ve Yöntem `new` anahtar sözcük mevcut gibi davranır.  
  
- Türetilmiş sınıftaki yöntemin önünde `new` anahtar sözcüğü varsa, yöntemi temel sınıftaki yönteminden bağımsız olarak tanımlanır.  
  
- Türetilmiş sınıftaki yönteminin önünde `override` anahtar sözcüğü varsa, türetilen sınıfın nesneleri temel sınıf yöntemi yerine bu yöntemi çağırır.  
  
- Temel sınıf yöntemi, `base` anahtar sözcüğü kullanılarak türetilmiş sınıfın içinden çağrılabilir.  
  
- `override`, Veanahtar`new` sözcükleri özellikler, Dizin oluşturucular ve olaylara de uygulanabilir. `virtual`  
  
 Varsayılan olarak, C# metotlar sanal değildir. Bir yöntem sanal olarak bildirilirse, yöntemi devralan herhangi bir sınıf kendi sürümünü uygulayabilir. Bir yöntemi sanal yapmak için, `virtual` değiştirici temel sınıfın yöntem bildiriminde kullanılır. Türetilmiş sınıf daha sonra `override` anahtar sözcüğünü kullanarak temel sanal yöntemi geçersiz kılabilir veya `new` anahtar sözcüğünü kullanarak temel sınıftaki sanal yöntemi gizleyebilirler. `override` Anahtar sözcüğünün`new` veya anahtar sözcüğünün hiçbiri belirtilmemişse, derleyici bir uyarı vermez ve türetilmiş sınıftaki yöntem temel sınıftaki yöntemi gizler.  
  
 Bu uygulamada bunu göstermek için, şirket a 'nın programın kullandığı adlı `GraphicsClass`bir sınıf oluşturduğunu varsayalım. Aşağıdakiler aşağıda verilmiştir `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Şirketiniz bu sınıfı kullanır ve yeni bir yöntem ekleyerek kendi sınıfınızı türetmeniz için kullanın:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Uygulamanız sorunlar olmadan kullanılır ve Şirket A, aşağıdaki koda benzeyen yeni bir sürümünü `GraphicsClass`yayınlar:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Yeni sürümü `GraphicsClass` artık adlı `DrawRectangle`bir yöntemi içerir. Başlangıçta, hiçbir şey gerçekleşmez. Yeni sürüm hala eski sürümle uyumlu. Dağıttığınız tüm yazılımlar, yeni sınıf bu bilgisayar sistemlerine yüklense bile çalışmaya devam eder. Yöntemine `DrawRectangle` yapılan tüm çağrılar, türetilmiş sınıfınıza sürümünüze başvurmasına devam edecektir.  
  
 Ancak, uygulamanızı yeni sürümünü `GraphicsClass`kullanarak yeniden derleyeceğinden, CS0108 derleyicisinden bir uyarı alırsınız. Bu uyarı, `DrawRectangle` yönteminizin uygulamanızda nasıl davranmasını istediğinizi göz önünde bulundurması gerektiğini bildirir.  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istiyorsanız `override` anahtar sözcüğünü kullanın:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Anahtar `override` sözcüğü, öğesinden `YourDerivedGraphicsClass` türetilmiş tüm nesnelerin türetilmiş sınıf sürümünü `DrawRectangle`kullanmasını sağlar. Öğesinden `YourDerivedGraphicsClass` türetilen nesneler, taban anahtar sözcüğünü kullanarak ' nin `DrawRectangle` temel sınıf sürümüne erişmeye devam edebilir:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istemiyorsanız, aşağıdaki noktalar geçerlidir. İki yöntem arasında karışıklık oluşmasını önlemek için yönteminizi yeniden adlandırabilirsiniz. Bu, zaman alan ve hataya açık olabilir ve bazı durumlarda pratik değildir. Ancak, projeniz nispeten küçükse, yöntemi yeniden adlandırmak için Visual Studio 'nun yeniden düzenleme seçeneklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [yeniden düzenleme sınıfları ve türleri (sınıf Tasarımcısı)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternatif olarak, türetilmiş sınıf tanımınızda anahtar sözcüğünü `new` kullanarak uyarıyı engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 `new` Anahtar sözcüğünün kullanılması derleyiciye tanımınızın taban sınıfta bulunan tanımı gizlediğini söyler. Bu varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve Yöntem seçimi  
 Bir yöntem bir sınıfta adlandırıldığında, C# derleyici, aynı ada sahip iki yöntem olduğunda ve geçilen parametre ile uyumlu olan parametreler gibi, çağrı ile uyumlu olduğunda çağırmak için en iyi yöntemi seçer. Aşağıdaki yöntemler uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 C# `DoWork` Bir örneği üzerinde çağrıldığında `Derived`, derleyici ilk olarak çağrıyı üzerinde başlangıçta belirtilen sürümlerle uyumlu hale getirmek üzere çalışır. `Derived` `DoWork` Geçersiz kılma yöntemleri bir sınıfta bildirildiği gibi düşünülmez, bir temel sınıfta belirtilen metodun yeni uygulamalarıdır. Yalnızca C# derleyici ' de `Derived` bir özgün metoda yönelik yöntem çağrısını eşleşemez, geçersiz kılınan bir yönteme yapılan çağrıyı aynı ada ve uyumlu parametrelere eşleştirmeye çalışır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Değişken `val` örtük olarak bir Double 'a dönüştürülebildiğinden, `DoWork(int)` C# derleyici yerine ' ı `DoWork(double)` çağırır. Bunu önlemenin iki yolu vardır. İlk olarak, sanal yöntemlerle aynı ada sahip yeni yöntemler bildirmemeye özen gösterin. İkinci olarak, örneğini C# `Derived` `Base`' a aktararak temel sınıf Yöntem listesinde arama yaparak derleyiciye sanal yöntemi çağırabilmeniz için talimat verebilirsiniz. Yöntemi sanal olduğu için, `DoWork(int)` üzerinde `Derived` uygulamasının uygulanması çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 `new` Ve`override`hakkında daha fazla örnek için bkz. [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Yöntemler](./methods.md)
- [Devralma](./inheritance.md)
