---
title: Geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: c85f5b6b4552dc4a10c7ad66b8f93331f97a8621
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196208"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
Dil C# , farklı kitaplıklarda [temel](../../language-reference/keywords/base.md) ve türetilmiş sınıflar arasında sürüm oluşturmanın, geriye dönük uyumluluğu geliştirebilir ve bakımını yapabilmesi için tasarlanmıştır. Bu, örneğin, türetilmiş bir sınıftaki üye ile aynı ada sahip bir temel [sınıfta](../../language-reference/keywords/class.md) yeni bir üyenin giriş tarafından C# tamamen desteklendiği ve beklenmeyen davranışlara neden olmadığı anlamına gelir. Ayrıca, bir yöntemin devralınan bir yöntemi geçersiz kılmak için bir yöntemin açıkça veya bir yöntemin devralınmış bir adlandırılmış yöntemi gizleyen yeni bir yöntem olup olmadığı anlamına gelir.  
  
 ' C#De, türetilmiş sınıflar temel sınıf yöntemleriyle aynı ada sahip yöntemler içerebilir.  
  
- Temel sınıf yöntemi tanımlanmış bir [sanal](../../language-reference/keywords/virtual.md)olmalıdır.  
  
- Türetilmiş sınıftaki yöntemin önünde [New](../../language-reference/keywords/new-modifier.md) veya [override](../../language-reference/keywords/override.md) anahtar sözcükleri yoksa, derleyici bir uyarı verecek ve Yöntem `new` anahtar sözcüğü var gibi davranır.  
  
- Türetilmiş sınıftaki yöntemi öncesinde `new` anahtar kelimesiyle, yöntemi temel sınıftaki yönteminden bağımsız olarak tanımlanır.  
  
- Türetilmiş sınıftaki yöntemin önünde `override` anahtar sözcüğü varsa, türetilen sınıfın nesneleri temel sınıf yöntemi yerine bu yöntemi çağırır.  
  
- Temel sınıf yöntemi, `base` anahtar sözcüğü kullanılarak türetilmiş sınıfın içinden çağrılabilir.  
  
- `override`, `virtual`ve `new` anahtar sözcükleri özellikler, Dizin oluşturucular ve olaylar için de uygulanabilir.  
  
 Varsayılan olarak, C# metotlar sanal değildir. Bir yöntem sanal olarak bildirilirse, yöntemi devralan herhangi bir sınıf kendi sürümünü uygulayabilir. Bir yöntemi sanal yapmak için, taban sınıfının yöntem bildiriminde `virtual` değiştiricisi kullanılır. Türetilmiş sınıf daha sonra, `override` anahtar sözcüğünü kullanarak temel sanal yöntemi geçersiz kılabilir veya `new` anahtar sözcüğünü kullanarak temel sınıftaki sanal yöntemi gizleyebilirsiniz. `override` anahtar sözcüğünün ne de `new` anahtar sözcüğü belirtilmemişse, derleyici bir uyarı vermez ve türetilmiş sınıftaki yöntem temel sınıftaki yöntemi gizler.  
  
 Bu uygulamada bunu göstermek için, Şirket A 'nın programınızın kullandığı `GraphicsClass`adlı bir sınıf oluşturduğunu varsayalım. `GraphicsClass`aşağıda verilmiştir:  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Şirketiniz bu sınıfı kullanır ve yeni bir yöntem ekleyerek kendi sınıfınızı türetmeniz için kullanın:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Uygulamanız sorunlar olmadan kullanılır, Şirket A `GraphicsClass`yeni bir sürümünü yayınlar, bu da aşağıdaki koda benzer:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 `GraphicsClass` yeni sürümü artık `DrawRectangle`adlı bir yöntemi içerir. Başlangıçta, hiçbir şey gerçekleşmez. Yeni sürüm hala eski sürümle uyumlu. Dağıttığınız tüm yazılımlar, yeni sınıf bu bilgisayar sistemlerine yüklense bile çalışmaya devam eder. `DrawRectangle` yönteme yapılan tüm çağrılar, türetilmiş sınıfınıza sürümünüze başvurmasına devam edecektir.  
  
 Ancak, `GraphicsClass`yeni sürümünü kullanarak uygulamanızı yeniden derleydükten sonra, CS0108 derleyicisinden bir uyarı alırsınız. Bu uyarı, `DrawRectangle` yönteminizin uygulamanızda nasıl davranmasını istediğinizi dikkate almanız gerektiğini bildirir.  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istiyorsanız `override` anahtar sözcüğünü kullanın:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 `override` anahtar sözcüğü, `YourDerivedGraphicsClass` türetilmiş tüm nesnelerin `DrawRectangle`türetilmiş sınıf sürümünü kullanmasını sağlar. `YourDerivedGraphicsClass` türetilen nesneler, temel anahtar sözcüğünü kullanarak `DrawRectangle` temel sınıf sürümüne erişmeye devam edebilir:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Yönteminizin yeni temel sınıf yöntemini geçersiz kılmasını istemiyorsanız, aşağıdaki noktalar geçerlidir. İki yöntem arasında karışıklık oluşmasını önlemek için yönteminizi yeniden adlandırabilirsiniz. Bu, zaman alan ve hataya açık olabilir ve bazı durumlarda pratik değildir. Ancak, projeniz nispeten küçükse, yöntemi yeniden adlandırmak için Visual Studio 'nun yeniden düzenleme seçeneklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [yeniden düzenleme sınıfları ve türleri (sınıf Tasarımcısı)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternatif olarak, türetilmiş sınıf tanımınızda `new` anahtar sözcüğünü kullanarak uyarıyı engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 `new` anahtar sözcüğünü kullanmak derleyiciye, tanımınızın taban sınıfta bulunan tanımı gizlediğini belirtir. Bu, varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve Yöntem seçimi  
 Bir yöntem bir sınıfta adlandırıldığında, C# derleyici, aynı ada sahip iki yöntem olduğunda ve geçilen parametre ile uyumlu olan parametreler gibi, çağrı ile uyumlu olduğunda çağırmak için en iyi yöntemi seçer. Aşağıdaki yöntemler uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 `DoWork` bir `Derived`örneğinde çağrıldığında, C# derleyici ilk olarak çağrıyı `Derived`üzerinde ilk olarak belirtilen `DoWork` sürümleriyle uyumlu hale getirmek üzere çalışır. Geçersiz kılma yöntemleri bir sınıfta bildirildiği gibi düşünülmez, bir temel sınıfta belirtilen metodun yeni uygulamalarıdır. Yalnızca C# derleyici, `Derived` üzerindeki bir özgün yönteme yönelik yöntem çağrısını eşleşemez, geçersiz kılınan bir yönteme yapılan çağrıyı aynı ada ve uyumlu parametrelere eşleştirmeye çalışır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 `val` değişkeni bir Double öğesine örtük olarak dönüştürülebildiğinden, C# derleyici `DoWork(int)`yerine `DoWork(double)` çağırır. Bunu önlemenin iki yolu vardır. İlk olarak, sanal yöntemlerle aynı ada sahip yeni yöntemler bildirmemeye özen gösterin. İkinci olarak, `Derived` örneğini `Base`C# kaldırarak temel sınıf Yöntem listesinde arama yaparak derleyiciye sanal yöntemi çağırabilmeniz için talimat verebilirsiniz. Yöntem sanal olduğu için, `Derived` üzerindeki `DoWork(int)` uygulanması çağrılacaktır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 `new` ve `override`daha fazla örnek için bkz. [override ve New anahtar sözcüklerini ne zaman kullanacağınızı bilme](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Yöntemler](./methods.md)
- [Devralma](./inheritance.md)
