---
title: Geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma-C# Programlama Kılavuzu
description: C# ' de temel ve türetilmiş sınıflar için sürüm oluşturma hakkında bilgi edinin ve bir yöntemin devralınmış bir yöntemi geçersiz kılmayı veya gizlemeyi amaçladığı bir yöntemi nasıl belirteceğinizi öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: c2630741e1055a14dd5b9e4445d660cfd68891b0
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863870"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
C# dili, farklı kitaplıklarda [temel](../../language-reference/keywords/base.md) ve türetilmiş sınıflar arasında sürüm oluşturmanın, geriye dönük uyumluluğu geliştirebilir ve bakımını yapabilmesi için tasarlanmıştır. Bu, örneğin, türetilmiş bir sınıftaki üye ile aynı ada sahip bir temel [sınıfta](../../language-reference/keywords/class.md) yeni bir üyenin giriş C# tarafından tamamen desteklendiğinden ve beklenmeyen davranışa yol açmadığı anlamına gelir. Ayrıca, bir yöntemin devralınan bir yöntemi geçersiz kılmak için bir yöntemin açıkça veya bir yöntemin devralınmış bir adlandırılmış yöntemi gizleyen yeni bir yöntem olup olmadığı anlamına gelir.  
  
 C# ' de, türetilmiş sınıflar temel sınıf yöntemleriyle aynı ada sahip yöntemler içerebilir.  

- Türetilmiş sınıftaki yöntemin önünde [Yeni](../../language-reference/keywords/new-modifier.md) veya [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcükleri yoksa, derleyici bir uyarı verecek ve Yöntem `new` anahtar sözcük mevcut gibi davranır.  
  
- Türetilmiş sınıftaki yöntemin önünde `new` anahtar sözcüğü varsa, yöntemi temel sınıftaki yönteminden bağımsız olarak tanımlanır.  
  
- Türetilmiş sınıftaki yönteminin önünde `override` anahtar sözcüğü varsa, türetilen sınıfın nesneleri temel sınıf yöntemi yerine bu yöntemi çağırır.  

- `override`Anahtar sözcüğünü türetilmiş sınıftaki yöntemine uygulamak için, temel sınıf yönteminin tanımlanmış [sanal](../../language-reference/keywords/virtual.md)olması gerekir.
  
- Temel sınıf yöntemi, anahtar sözcüğü kullanılarak türetilmiş sınıfın içinden çağrılabilir `base` .  
  
- `override`, `virtual` Ve `new` anahtar sözcükleri özellikler, Dizin oluşturucular ve olaylara de uygulanabilir.  
  
 Varsayılan olarak, C# yöntemleri sanal değildir. Bir yöntem sanal olarak bildirilirse, yöntemi devralan herhangi bir sınıf kendi sürümünü uygulayabilir. Bir yöntemi sanal yapmak için, `virtual` değiştirici temel sınıfın yöntem bildiriminde kullanılır. Türetilmiş sınıf daha sonra anahtar sözcüğünü kullanarak temel sanal yöntemi geçersiz kılabilir `override` veya anahtar sözcüğünü kullanarak temel sınıftaki sanal yöntemi gizleyebilirler `new` . `override`Anahtar sözcüğünün veya anahtar sözcüğünün hiçbiri `new` belirtilmemişse, derleyici bir uyarı vermez ve türetilmiş sınıftaki yöntem temel sınıftaki yöntemi gizler.  
  
 Bu uygulamada bunu göstermek için, Şirket A 'nın programın kullandığı adlı bir sınıf oluşturduğunu varsayalım `GraphicsClass` . Aşağıdakiler aşağıda verilmiştir `GraphicsClass` :  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Şirketiniz bu sınıfı kullanır ve yeni bir yöntem ekleyerek kendi sınıfınızı türetmeniz için kullanın:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Uygulamanız sorunlar olmadan kullanılır ve Şirket A, aşağıdaki koda benzeyen yeni bir sürümünü yayınlar `GraphicsClass` :  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 Yeni sürümü `GraphicsClass` artık adlı bir yöntemi içerir `DrawRectangle` . Başlangıçta, hiçbir şey gerçekleşmez. Yeni sürüm hala eski sürümle uyumlu. Dağıttığınız tüm yazılımlar, yeni sınıf bu bilgisayar sistemlerine yüklense bile çalışmaya devam eder. Yöntemine yapılan tüm çağrılar `DrawRectangle` , türetilmiş sınıfınıza sürümünüze başvurmasına devam edecektir.  
  
 Ancak, uygulamanızı yeni sürümünü kullanarak yeniden derleyeceğinden, `GraphicsClass` CS0108 derleyicisinden bir uyarı alırsınız. Bu uyarı, yönteminizin uygulamanızda nasıl davranmasını istediğinizi göz önünde bulundurması gerektiğini bildirir `DrawRectangle` .  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istiyorsanız `override` anahtar sözcüğünü kullanın:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 `override`Anahtar sözcüğü, öğesinden türetilmiş tüm nesnelerin `YourDerivedGraphicsClass` türetilmiş sınıf sürümünü kullanmasını sağlar `DrawRectangle` . Öğesinden türetilen nesneler, `YourDerivedGraphicsClass` `DrawRectangle` taban anahtar sözcüğünü kullanarak ' nin temel sınıf sürümüne erişmeye devam edebilir:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istemiyorsanız, aşağıdaki noktalar geçerlidir. İki yöntem arasında karışıklık oluşmasını önlemek için yönteminizi yeniden adlandırabilirsiniz. Bu, zaman alan ve hataya açık olabilir ve bazı durumlarda pratik değildir. Ancak, projeniz nispeten küçükse, yöntemi yeniden adlandırmak için Visual Studio 'nun yeniden düzenleme seçeneklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [yeniden düzenleme sınıfları ve türleri (sınıf Tasarımcısı)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternatif olarak, `new` türetilmiş sınıf tanımınızda anahtar sözcüğünü kullanarak uyarıyı engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 `new`Anahtar sözcüğünün kullanılması derleyiciye tanımınızın taban sınıfta bulunan tanımı gizlediğini söyler. Bu, varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve Yöntem seçimi  
 Bir yöntem bir sınıfta adlandırıldığında, C# derleyicisi, aynı ada sahip iki yöntem olduğunda ve geçilen parametre ile uyumlu olan parametreler gibi, çağrı ile uyumlu olduğunda çağırmak için en iyi yöntemi seçer. Aşağıdaki yöntemler uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 `DoWork`, Bir örneği üzerinde çağrıldığında `Derived` , C# derleyicisi ilk olarak çağrıyı üzerinde ilk olarak bildirildiği sürümlerle uyumlu hale getirme denenir `DoWork` `Derived` . Geçersiz kılma yöntemleri bir sınıfta bildirildiği gibi düşünülmez, bir temel sınıfta belirtilen metodun yeni uygulamalarıdır. Yalnızca C# derleyicisi ' de bir özgün metoda yönelik yöntem çağrısını eşleşemez, `Derived` geçersiz kılınan bir yönteme yapılan çağrıyı aynı ada ve uyumlu parametrelere eşleştirmeye çalışır. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Değişken örtük olarak `val` bir Double 'a dönüştürülebildiğinden, C# derleyicisi yerine ' ı çağırır `DoWork(double)` `DoWork(int)` . Bunu önlemenin iki yolu vardır. İlk olarak, sanal yöntemlerle aynı ada sahip yeni yöntemler bildirmemeye özen gösterin. İkincisi, C# derleyicisine, örneğini ' a aktararak temel sınıf yöntemi listesinde arama yaparak sanal yöntemi çağırabilmeniz için talimat verebilirsiniz `Derived` `Base` . Yöntemi sanal olduğu için, üzerinde uygulamasının uygulanması `DoWork(int)` `Derived` çağrılır. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Ve hakkında daha fazla örnek için `new` `override` bkz. [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Yöntemler](./methods.md)
- [Devralma](./inheritance.md)
