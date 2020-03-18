---
title: Geçersiz Kılma ve Yeni Anahtar Kelimelerle Sürümleme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 089d5d7c7a95e2de4629f53255d9d9790fd5508a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705398"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
C# dili, farklı kitaplıklarda [taban](../../language-reference/keywords/base.md) ve türetilmiş sınıflar arasındaki sürümgeliştirmenin gelişebileceği ve geriye dönük uyumluluğu koruyabilmesi için tasarlanmıştır. Bu, örneğin, türemiş bir sınıftaki bir üyeyle aynı ada sahip bir taban [sınıfa](../../language-reference/keywords/class.md) yeni bir üyenin tanıtılmasının tamamen C# tarafından desteklenildiği ve beklenmeyen davranışlara yol açmadığı anlamına gelir. Ayrıca, bir sınıfın, bir yöntemin devralınan bir yöntemi geçersiz kılmaya mı yönelik olduğunu yoksa benzer adlandırılmış bir yöntemi gizleyen yeni bir yöntem olup olmadığını açıkça belirtmesi gerektiği anlamına gelir.  
  
 C#'da türemiş sınıflar taban sınıf yöntemleriyle aynı ada sahip yöntemler içerebilir.  
  
- Taban sınıf yöntemi [sanal](../../language-reference/keywords/virtual.md)olarak tanımlanmalıdır.  
  
- Türemiş sınıftaki yöntem yeni veya [geçersiz kılınan](../../language-reference/keywords/override.md) anahtar kelimelerden önce değilse, derleyici bir uyarı `new` verir ve yöntem anahtar sözcük hazırmış gibi çalışır. [new](../../language-reference/keywords/new-modifier.md)  
  
- Türemiş sınıftaki yöntem `new` anahtar sözcükten önce geliyorsa, yöntem taban sınıftaki yöntemden bağımsız olarak tanımlanır.  
  
- Türemiş sınıftaki yöntem `override` anahtar sözcükten önce geliyorsa, türemiş sınıfın nesneleri taban sınıf yöntemi yerine bu yöntemi çağırır.  
  
- Taban sınıf yöntemi, türetilmiş sınıfın içinden anahtar sözcük `base` kullanılarak çağrılabilir.  
  
- , `override` `virtual`ve `new` anahtar kelimeler de özellikleri, dizinleyiciler ve olaylar uygulanabilir.  
  
 Varsayılan olarak, C# yöntemleri sanal değildir. Bir yöntem sanal olarak bildirilirse, yöntemi devralan herhangi bir sınıf kendi sürümünü uygulayabilir. Bir yöntemi sanal yapmak `virtual` için, değiştirici taban sınıfın yöntem bildiriminde kullanılır. Türemiş sınıf daha sonra `override` anahtar sözcüğü kullanarak temel sanal yöntemi geçersiz kılabilir `new` veya anahtar sözcüğü kullanarak temel sınıfta sanal yöntemi gizleyebilir. Ne `override` anahtar kelime ne `new` de anahtar kelime belirtilmemişse, derleyici bir uyarı yayımlar ve türemiş sınıftaki yöntem yöntem taban sınıfta gizlenecektir.  
  
 Uygulamada bunu göstermek için, Bir an için A Şirketinin programınızın kullandığı adlandırılmış `GraphicsClass`bir sınıf oluşturduğunu varsayalım. Aşağıdaki gibidir: `GraphicsClass`  
  
 [!code-csharp[csProgGuideInheritance#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#27)]  
  
 Şirketiniz bu sınıfı kullanır ve yeni bir yöntem ekleyerek kendi sınıfınızı türetmek için kullanırsınız:  
  
 [!code-csharp[csProgGuideInheritance#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#28)]  
  
 Uygulamanız, Şirket A aşağıdaki kodu andıran `GraphicsClass`yeni bir sürümünü yayımlayana kadar sorunsuz kullanılır:  
  
 [!code-csharp[csProgGuideInheritance#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#29)]  
  
 `GraphicsClass` Şimdi yeni sürümü adlı `DrawRectangle`bir yöntem içerir. Başlangıçta hiçbir şey olmuyor. Yeni sürüm hala ikili eski sürümü ile uyumludur. Dağıttığınız tüm yazılımlar, bu bilgisayar sistemlerinde yeni sınıf yüklü olsa bile çalışmaya devam edecektir. Yönteme `DrawRectangle` varolan tüm aramalar, türemiş sınıfınızda sürümünüzü referans almaya devam edecektir.  
  
 Ancak, en kısa sürede yeni sürümünü `GraphicsClass`kullanarak uygulamanızı yeniden derlemek , derleyici, CS0108 bir uyarı alacaksınız. Bu uyarı, uygulamanızda yönteminizin `DrawRectangle` nasıl bir şekilde olmasını istediğinizi düşünmeniz gerektiğini bildirir.  
  
 Yönteminizin yeni taban sınıf yöntemini geçersiz kMasını istiyorsanız, `override` anahtar sözcüğü kullanın:  
  
 [!code-csharp[csProgGuideInheritance#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#30)]  
  
 Anahtar `override` kelime, türetilen `YourDerivedGraphicsClass` nesnelerin `DrawRectangle`türetilmiş sınıf sürümünü kullanmasını sağlar. Türetilen `YourDerivedGraphicsClass` nesneler, temel anahtar sözcüğü `DrawRectangle` kullanarak temel sınıf sürümüne erişebilir:  
  
 [!code-csharp[csProgGuideInheritance#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#44)]  
  
 Yönteminizin yeni taban sınıf yöntemini geçersiz kmasını istemiyorsanız, aşağıdaki hususlar uygulanır. İki yöntem arasındaki karışıklığı önlemek için yönteminizi yeniden adlandırabilirsiniz. Bu zaman alıcı ve hata eğilimli olabilir ve sadece bazı durumlarda pratik değil. Ancak, projeniz nispeten küçükse, yöntemi yeniden adlandırmak için Visual Studio'nun Yeniden Düzenleme seçeneklerini kullanabilirsiniz. Daha fazla bilgi için bkz: [ReFactoring Sınıfları ve Türleri (Sınıf Tasarımcısı)](/visualstudio/ide/class-designer/refactoring-classes-and-types).  
  
 Alternatif olarak, türemiş sınıf tanımınızda `new` anahtar kelimeyi kullanarak uyarıyı engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideInheritance#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#31)]  
  
 Anahtar `new` sözcüğün kullanılması derleyiciye, tanımınızın taban sınıfta bulunan tanımı gizlediğini söyler. Bu varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve Yöntem Seçimi  
 Bir sınıfta bir yöntem adlandığında, C# derleyicisi, aynı ada sahip iki yöntem ve geçirilen parametreyle uyumlu parametreler gibi birden fazla yöntem çağrıyla uyumluysa, aramak için en iyi yöntemi seçer. Aşağıdaki yöntemler uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#32)]  
  
 Bir `DoWork` örneğinde `Derived`çağrıldığında, C# derleyicisi ilk olarak aramayı ilk `DoWork` olarak bildirilen `Derived`sürümlerle uyumlu hale getirmeye çalışacaktır. Geçersiz kılma yöntemleri bir sınıfta beyan edildiği gibi kabul edilmez, bunlar taban sınıfa bildirilen bir yöntemin yeni uygulamalarıdır. Yalnızca C# derleyicisi yöntem çağrısını özgün `Derived` bir yöntemle eşleştiremezse, çağrıyı aynı ada ve uyumlu parametrelerle geçersiz kılınan bir yöntemle eşleştirmeye çalışır. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#33)]  
  
 Değişken `val` örtülü olarak çifte dönüştürülebildiği için, C# `DoWork(double)` derleyicisi `DoWork(int)`. Bunu önlemenin iki yolu vardır. İlk olarak, sanal yöntemlerle aynı ada sahip yeni yöntemler bildirmekten kaçının. İkinci olarak, C# derleyicisine, `Derived` `Base`'' örneğini döküm yaparak taban sınıf yöntem listesinde arama yaparak sanal yöntemi aramasını talimatı verebilirsiniz. Yöntem sanal olduğundan, `DoWork(int)` on `Derived` uygulaması çağrılacaktır. Örnek:  
  
 [!code-csharp[csProgGuideInheritance#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#34)]  
  
 Daha fazla `new` örnek `override`için , [override ve Yeni Anahtar Kelimeler ne zaman kullanılacağını bilmek](./knowing-when-to-use-override-and-new-keywords.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Yöntemler](./methods.md)
- [Devralma](./inheritance.md)
