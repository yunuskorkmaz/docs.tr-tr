---
title: Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 5dfed1c4a7e68bbe112a136260bf95ba0826392d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178383"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
C# dili tasarlanmıştır böylece sürüm arasında [temel](../../../csharp/language-reference/keywords/base.md) ve türetilmiş sınıfları farklı kitaplıklarında evrim geçiren ve geriye dönük uyumluluk sağlamak. Örneğin, yani yeni üyesi temel sunulmasıyla [sınıfı](../../../csharp/language-reference/keywords/class.md) türetilmiş bir sınıf üyesi olarak aynı ada sahip tamamen C# tarafından desteklenir ve beklenmeyen davranışlara yol değil. Ayrıca, bir sınıf devralınan bir yöntemi geçersiz kılmak için bir yöntem amaçlanmamıştır veya yöntemi devralınan bir yöntemi benzer ada gizler yeni bir yöntem olup olmadığını açıkça belirtmelidir anlamına gelir.  
  
 C# ' ta türetilmiş sınıflar temel sınıf yöntemleri olarak aynı ada sahip yöntem içerebilir.  
  
-   Temel sınıf yöntemini tanımlanmalıdır [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Yöntem türetilmiş sınıftaki öncesinde, [yeni](../../../csharp/language-reference/keywords/new.md) veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükler, derleyici bir uyarı verir ve yöntem davranacağını gibi `new` anahtar sözcüğü.  
  
-   Türetilmiş sınıftaki yöntemi ile öncesinde, `new` anahtar sözcüğü, yöntem temel sınıfta yöntemin bağımsız olan olarak tanımlanır.  
  
-   Türetilmiş sınıftaki yöntemi ile öncesinde, `override` anahtar sözcüğü, türetilmiş sınıfın nesneleri bir temel sınıf yöntemi yerine bu yöntem çağıracaktır.  
  
-   Temel sınıf yöntemini öğesinden türetilmiş bir sınıf kullanılarak içinde çağrılabilir `base` anahtar sözcüğü.  
  
-   `override`, `virtual`, Ve `new` anahtar sözcükler, ayrıca özellikler, dizin oluşturucular ve olaylar için uygulanabilir.  
  
 Varsayılan olarak, C# yöntemler sanal değildir. Bir yöntemi sanal olarak bildirilirse, yönteminden devralan herhangi bir sınıf kendi sürüm uygulayabilirsiniz. Sanal bir yöntem yapmak `virtual` değiştirici, temel sınıf yöntemi bildiriminde kullanılır. Türetilmiş sınıf ardından temel sanal yöntemi kullanarak kılabilirsiniz `override` anahtar sözcüğü veya gizleme kullanarak temel sınıf sanal yöntemi `new` anahtar sözcüğü. Kullanılmazsa `override` anahtar sözcüğü ya da `new` anahtar sözcüğü belirtildiğinde, derleyici bir uyarı verir ve yöntem temel sınıfta türetilmiş sınıf yöntemi gizler.  
  
 Bu uygulamada göstermek için bir süre Şirket A adlı bir sınıf oluşturduğunu varsayalım `GraphicsClass`, programınızı kullanır. Aşağıdaki `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Bu sınıf, şirketinizin kullandığı ve yeni yöntem ekleme kendi sınıf türetmek için kullanın:  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Yeni bir sürümü şirketi serbest kadar uygulamanız sorunsuz kullanılan `GraphicsClass`, aşağıdaki kod benzer:  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 Yeni sürümünü `GraphicsClass` artık adında bir yöntem içeriyorsa `DrawRectangle`. Başlangıçta, hiçbir şey olmaz. Yeni sürümü, eski sürümü ile yine ikili uyumlu değildir. Yeni bir sınıf, bu bilgisayar sistemlerinde yüklü olsa bile dağıttığınız herhangi bir yazılım çalışmaya devam eder. Var olan yöntem çağrıları `DrawRectangle` , türetilmiş sınıf içinde sürümünüzü başvurmaya devam eder.  
  
 Ancak, olarak yeni sürümünü kullanarak uygulamanızı yeniden derlemeniz yakında `GraphicsClass`, derleyici, CS0108 bir uyarı alırsınız. Bu uyarı nasıl istediğinizi düşünün olduğunu bildirir, `DrawRectangle` uygulamanızda davranmaya yöntemi.  
  
 Yeni bir temel sınıf yöntemini geçersiz kılmak için yönteminizi istiyorsanız kullanın `override` anahtar sözcüğü:  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` Anahtar sözcüğü yapar herhangi bir nesne öğesinden türetilen emin `YourDerivedGraphicsClass` türetilmiş sınıf sürümünü kullanacak `DrawRectangle`. Türetilmiş nesneler `YourDerivedGraphicsClass` temel sınıf sürümü erişmeye devam edebilirsiniz `DrawRectangle` base anahtar sözcüğü kullanarak:  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Yeni bir temel sınıf yöntemini geçersiz kılmak için yönteminizi istemiyorsanız, aşağıdaki maddeler geçerlidir. İki yöntem arasındaki Karışıklığı önlemek için yöntem yeniden adlandırabilirsiniz. Bu, zaman alan ve hata yapmaya açık ve değil, bazı durumlarda kullanışlı olabilir. Projenizi görece küçük ise, yöntem yeniden adlandırmak için Visual Studio'nun yeniden düzenleme seçeneklerini kullanabilirsiniz. Daha fazla bilgi için [yeniden düzenleme sınıfları ve türleri (Sınıf Tasarımcısı)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternatif olarak, anahtar sözcüğü kullanarak uyarı engel olabilir `new` , türetilmiş bir sınıf tanımı içinde:  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Kullanarak `new` anahtar sözcüğü derleyiciye tanımınızı temel sınıfta yer alan tanımı gizler. Bu varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve yöntemi seçimi  
 Bir sınıf üzerinde adlı bir yöntemi, C# derleyicisi gibi birden fazla metot çağrısı ile uyumlu ise, çağrılacak en iyi yöntem seçer. aynı ada ve geçirilen parametre ile uyumlu olan parametreleri içeren iki yöntem olduğunda. Aşağıdaki yöntemlerden uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Zaman `DoWork` örneğinde adlı `Derived`, C# Derleyici ilk çağrı sürümleriyle uyumlu hale getirmek deneyecek `DoWork` ilk olarak bildirilmiş `Derived`. Geçersiz kılma yöntemleri sınıfta bildirilen dikkate alınmaz, bunlar bir yöntem temel sınıfta bildirilen yeni uygulamalarıdır. Yalnızca C# derleyicisi bir asıl yöntemi için yöntem çağrısının üzerinde eşleyemiyorsanız `Derived` uyumlu parametreler ve aynı ada sahip bir geçersiz kılınan yöntemine çağrı eşleşecek şekilde çalışacaktır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Çünkü değişken `val` double'örtülü olarak dönüştürülebilir C# Derleyici çağrıları `DoWork(double)` yerine `DoWork(int)`. Bunu önlemek için iki yolu vardır. İlk olarak, yeni yöntemlerle aynı adı taşıyan sanal yöntemler bildirme kaçının. İkinci olarak, temel sınıf yöntemini listesi örneğini atayarak arama yaparak sanal yöntemini çağırmak için C# Derleyici bildirebilirsiniz `Derived` için `Base`. Sanal bir yöntem olduğundan yürütmesinin `DoWork(int)` üzerinde `Derived` olarak adlandırılır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Daha fazla örnek için `new` ve `override`, bkz: [bilerek, kullanım geçersiz kılma ve yeni anahtar sözcüklerle](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
