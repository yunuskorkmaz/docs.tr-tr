---
title: Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 2a6a6f59320d94cf97b1a07448000bd708d95559
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327557"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma (C# Programlama Kılavuzu)
C# dili tasarlanmış böylece sürüm oluşturma arasında [temel](../../../csharp/language-reference/keywords/base.md) ve farklı kitaplıkları türetilmiş sınıflarda gelişmesi ve geriye dönük uyumluluğu korumak. Örneğin, yani bir Base yeni bir üye giriş [sınıfı](../../../csharp/language-reference/keywords/class.md) türetilmiş bir sınıf üye olarak aynı ada sahip tamamen C# tarafından desteklenir ve beklenmeyen bir davranışa neden olmaz. Ayrıca, bir sınıf bir yöntem devralınan yöntemi geçersiz kılmak için tasarlanmıştır veya yöntemi devralınan bir yöntem benzer ada gizler yeni bir yöntemi olup olmadığını açıkça belirtmelidir anlamına gelir.  
  
 C# ' ta türetilmiş sınıfları, yöntemleri taban sınıf yöntemlerini aynı ada sahip içerebilir.  
  
-   Temel sınıf yöntemi tanımlanmalıdır [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Türetilmiş sınıf yönteminde öncesinde, [yeni](../../../csharp/language-reference/keywords/new.md) veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcükler, derleyici bir uyarı verecek ve yöntemi davranacak gibi `new` anahtar sözcüğü vardı.  
  
-   Türetilmiş sınıf yöntemi ile öncesinde, `new` anahtar sözcüğü, yöntemi temel sınıf yönteminde bağımsız olacak şekilde tanımlanır.  
  
-   Türetilmiş sınıf yöntemi ile öncesinde, `override` anahtar sözcüğü, türetilmiş sınıf nesnelerin temel sınıf yöntemi yerine bu yöntem çağıracaktır.  
  
-   Temel sınıf yöntemi öğesinden türetilmiş bir sınıf kullanılarak içinde çağrılabilir `base` anahtar sözcüğü.  
  
-   `override`, `virtual`, Ve `new` anahtar sözcükler, ayrıca özellikleri, dizin oluşturucular ve olayları için uygulanabilir.  
  
 Varsayılan olarak, C# yöntemleri sanal değildir. Bir yöntem olarak sanal bildirilirse yöntemi devralma herhangi bir sınıf kendi sürüm uygulayabilirsiniz. Bir yöntem sanal yapmak için `virtual` değiştiricisi temel sınıfın yöntem bildirimi kullanılır. Türetilmiş sınıf sonra temel sanal yöntemi kullanarak kılabilirsiniz `override` anahtar sözcüğü veya gizleme sanal yöntemi kullanarak temel sınıf `new` anahtar sözcüğü. Ne `override` anahtar sözcüğü veya `new` anahtar sözcüğü belirtildiğinde, derleyici bir uyarı verecek ve türetilmiş sınıf yöntemi temel sınıf yönteminde gizlenir.  
  
 Bu uygulamada göstermek için bir süre için Şirket A adlı bir sınıf oluşturdu varsayın `GraphicsClass`, hangi programınız kullanır. Aşağıdaki `GraphicsClass`:  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Bu sınıf, şirketinizin kullandığı ve yeni bir yöntem ekleme kendi sınıf Türetmenin kullanın:  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Şirket A yeni bir sürümünü yayımlar kadar uygulamanızın sorunsuz kullanılan `GraphicsClass`, aşağıdaki kodu benzer:  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 Yeni sürümü `GraphicsClass` şimdi adlı bir yöntem içerir `DrawRectangle`. Başlangıçta, hiçbir şey olmaz. Yeni sürümü, eski sürüm ile yine ikili uyumlu. Bu bilgisayar sistemlerinde yeni sınıf yüklü olsa bile dağıtmış olan herhangi bir yazılım çalışmaya devam eder. Varolan aramaların yöntemine `DrawRectangle` türetilmiş sınıfınızda sürümünüzü başvurmaya devam eder.  
  
 Ancak, sürede yeni sürümünü kullanarak uygulamanızı yeniden derleyin gibi `GraphicsClass`, derleyici, CS0108 bir uyarı alırsınız. Bu uyarı nasıl istediğinizi dikkate almanız gerekir bildirir, `DrawRectangle` uygulamanızda davranmasına yöntemi.  
  
 Yeni temel sınıf yöntemi geçersiz kılmak için yönteminizi istiyorsanız kullanın `override` anahtar sözcüğü:  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` Anahtar sözcüğü yapar herhangi bir nesne öğesinden türetilen emin `YourDerivedGraphicsClass` türetilmiş sınıf sürümünü kullanacak `DrawRectangle`. Nesneleri türetilen `YourDerivedGraphicsClass` temel sınıf sürümü erişmeye devam edebilirsiniz `DrawRectangle` base anahtar sözcüğü kullanarak:  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Yeni temel sınıf yöntemi geçersiz kılmak için yönteminizi istemiyorsanız, aşağıdaki maddeler geçerlidir. İki yöntem arasındaki Karışıklığı önlemek için yönteminizi yeniden adlandırabilirsiniz. Bu, çok zaman alır ve hatalara eğilimli ve bazı durumlarda pratik yalnızca olabilir. Projeniz görece küçük ise, yöntem yeniden adlandırmak için Visual Studio'nun Refactoring seçeneklerini kullanabilirsiniz. Daha fazla bilgi için bkz: [yeniden düzenleme sınıfları ve türleri (Sınıf Tasarımcısı)](/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Alternatif olarak, anahtar sözcüğünü kullanarak uyarı engel olabilirsiniz `new` türetilmiş bir sınıf tanımı'nda:  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Kullanarak `new` anahtar sözcüğü tanımınızı taban sınıf içinde yer alan tanımı gizler derleyici söyler. Bu varsayılan davranıştır.  
  
## <a name="override-and-method-selection"></a>Geçersiz kılma ve yöntemi seçimi  
 Bir yöntem bir sınıf üzerinde adlandırıldığında, C# Derleyici birden çok yöntem gibi çağrısı ile uyumlu ise çağırmak için en iyi yöntem seçer aynı ada ve geçirilen parametre ile uyumlu olan parametreleri iki yöntemle olduğunda. Aşağıdaki yöntemlerden uyumlu olacaktır:  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Zaman `DoWork` örneğinde adlı `Derived`, C# Derleyici çağrı sürümleriyle uyumlu hale getirmek önce deneyecek `DoWork` üzerinde ilk olarak bildirilen `Derived`. Geçersiz kılma yöntemleri bir sınıf üzerinde bildirilen olarak kabul edilmez, bunlar bir temel sınıf üzerinde bildirilmiş bir yöntemi yeni uygulamalarıdır. Yalnızca C# Derleyici özgün yöntemi için yöntem çağrısı üzerinde eşleştirme yapılamazsa `Derived` aynı adı ile uyumlu parametreler geçersiz kılınmış bir yöntemi çağrısı eşleşecek şekilde deneyin. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Çünkü değişkeni `val` double'dolaylı olarak dönüştürülebilir C# Derleyici çağrıları `DoWork(double)` yerine `DoWork(int)`. Bu durumu önlemek için iki yolu vardır. İlk olarak, sanal yöntemleri aynı ada sahip yeni yöntemleri bildirme kaçının. İkinci olarak, temel sınıf yöntemi listesi örneği, atama tarafından arama yaparak sanal yöntemini çağırmak için C# Derleyici söyleyebilirsiniz `Derived` için `Base`. Yöntemi sanal olduğundan uygulanması `DoWork(int)` üzerinde `Derived` çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Daha fazla örnekleri için `new` ve `override`, bkz: [kullanımı geçersiz kılma ve yeni anahtar sözcüklerin için bilerek olduğunda](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
