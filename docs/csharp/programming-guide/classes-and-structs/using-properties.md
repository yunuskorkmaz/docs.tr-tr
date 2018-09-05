---
title: Özellikleri Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: 50dda6a27081762a4e8b407ca5af94659b47da45
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515860"
---
# <a name="using-properties-c-programming-guide"></a>Özellikleri Kullanma (C# Programlama Kılavuzu)
Özellikler, alanlar ve yöntemler hem yönlerini birleştirin. Bir alan için bir özelliği bir nesnenin kullanıcıya görünen özelliğine erişmek, aynı sözdizimini gerektirir. Temsil eden bir veya iki kod blokları için uygulayan bir sınıfın özelliğidir bir [alma](../../../csharp/language-reference/keywords/get.md) erişimci veya [ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimcisi. Kod bloğu için `get` erişimci özelliği okunduğunda yürütülür; kod engellemek için `set` erişimci özelliği yeni bir değer atandığında yürütülür. Bir özellik olmadan bir `set` erişimci salt okunur kabul edilir. Bir özellik olmadan bir `get` salt yazılır erişimci kabul edilir. Her iki erişimcisi olan okuma-yazma özelliğidir.  
  
 Alanları özellikleri değişkenleri olarak sınıflandırılan değil. Bu nedenle, bir özellik olarak geçirilemez bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi.  
  
 Özellikleri, pek çok kullanımı vardır: bir değişiklik; izin vermeden önce verileri doğrulayabilirsiniz şeffaf bir şekilde burada verileri gerçekte bir veritabanı gibi diğer bazı kaynak alınır bir sınıf verilerini açığa çıkarabilir; Olay bildirmek veya diğer alanları değerinin değiştirilmesi gibi veri değiştirildiğinde, bunlar bir eylem sürebilir.  
  
 Özellikler alanı erişim düzeyini belirterek sınıfı blokta bildirilen, özelliğin türü tarafından izlenen, özellik adından önce gelen ve bildiren bir kod bloğu tarafından izlenen bir `get`-erişimci veya `set` erişimcisi. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Bu örnekte, `Month` bir özellik olarak, bu nedenle bildirildiği `set` erişimcisi emin olun `Month` değeri 1 ile 12 arasında ayarlanır. `Month` Özelliği, gerçek değer izlemek için özel bir alan kullanır. Bir özelliğin veri gerçek konumunu genellikle özelliğin "yedekleme deposu." adlandırılır Özel alanları bir yedekleme deposu kullanmak özellikler yaygındır. Alan, yalnızca özelliği çağırarak değiştirilebilir emin olmak için özel olarak işaretlenir. Genel ve özel erişim kısıtlamaları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Otomatik uygulanan özellikler basit özellik bildirimleri için Basitleştirilmiş söz dizimi sağlar. Daha fazla bilgi için [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Get erişimcisi  
 Gövdesi `get` erişimci, bir yöntemin benzer. Bu özellik türünde bir değer döndürmesi gerekir. Yürütülmesini `get` alanın değerini okumak için erişimci eşdeğerdir. Örneğin, ne zaman, döndürüyor özel değişkeninden `get` erişimcisi ve en iyi duruma getirme etkinleştirildiğini, çağrı `get` yöntem çağrısının zahmetine olduğundan erişimci yöntemi derleyici tarafından satır içine alınmış. Ancak, bir sanal `get` derleyici derleme zamanında hangi yöntemin gerçekten çağrılabilir çalışma zamanında bilmediğinden erişimci yöntemi satır içine alınmış olamaz. Aşağıda bir `get` özel bir alanın değerini döndüren bir erişimci `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Size özelliği dışında atama hedefi olarak başvurduğunuzda `get` erişimci özelliğin değerini okumak için çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 `get` Erişimci bitmelidir bir [dönüş](../../../csharp/language-reference/keywords/return.md) veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi ve denetimi devre dışı erişimcisinin gövdesi Akış olamaz.  
  
 Kullanarak bir nesnenin durumunu değiştirmek için hatalı bir programlama stili, `get` erişimcisi. Örneğin, aşağıdaki erişimci yan etkisi, her nesnenin durumunu değiştirme üretir, `number` alan erişildiğinde.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 `get` Erişimci alan değeri döndürür veya bu işlem ve döndürün için kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 Bir değere atamazsanız kesimdeki önceki kod, `Name` özelliği, a. değeri döndürecektir  
  
## <a name="the-set-accessor"></a>Ayarlama erişimcisi  
 `set` Erişimcisi, dönüş türü olan bir yöntem benzer [void](../../../csharp/language-reference/keywords/void.md). Adlı bir örtük parametreyi kullanan `value`, türü özelliği türüdür. Aşağıdaki örnekte, bir `set` erişimci eklenir `Name` özelliği:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Özellik için bir değer atadığınızda `set` erişimci, yeni değer sağlayan bir bağımsız değişkeni kullanılarak çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Örtük parametre adı kullanmak için bir hata olduğunu `value`, bir yerel değişken bildiriminde'için bir `set` erişimcisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Özellikler olarak işaretlenebilir `public`, `private`, `protected`, `internal`, `protected internal` veya `private protected`. Bu erişim değiştiricileri kullanıcılar sınıf özelliği nasıl erişebileceğiniz tanımlayın. `get` Ve `set` erişimcileri aynı özelliği için farklı erişim değiştiricilere sahip olabilir. Örneğin, `get` olabilir `public` salt okunur dışından erişim türü izin vermek ve `set` olabilir `private` veya `protected`. Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir özellik kullanarak statik bir özellik olarak bildirilmelidir `static` anahtar sözcüğü. Sınıfının bir örneğini bulunuyor olsa bile bu özellik kullanılabilir için herhangi bir zamanda yapar. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir özellik kullanarak sanal bir özellik olarak işaretlenebilir [sanal](../../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü. Bu kullanarak özellik davranışı geçersiz kılmak türetilmiş sınıfları sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü. Bu seçenekler hakkında daha fazla bilgi için bkz. [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Sanal bir özelliği geçersiz kılmak için bir özelliği de olabilir [korumalı](../../../csharp/language-reference/keywords/sealed.md), türetilmiş sınıflar için artık sanal olduğunu belirtin. Son olarak, bir özellik bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md). Bu sınıfta hiç uygulama yok ve türetilen sınıflar, kendi uygulama yazmanız gereken anlamına gelir. Bu seçenekler hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Kullanılacak bir hata olduğunu bir [sanal](../../../csharp/language-reference/keywords/virtual.md), [soyut](../../../csharp/language-reference/keywords/abstract.md), veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi bir erişimci bir [statik](../../../csharp/language-reference/keywords/static.md) özelliği.  
  
## <a name="example"></a>Örnek  
 Bu örnek, örnek, statik ve salt okunur özelliklerini gösterir. Bunu klavyeden artışlarla çalışan adını kabul eder `NumberOfEmployees` 1 ve görüntüler çalışan adı ve numarası.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, türetilmiş sınıf içinde aynı ada sahip başka bir özellik tarafından gizlenen bir taban sınıftaki bir özelliğe erişmek nasıl gösterir.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Önceki örnekte önemli noktalar şunlardır:  
  
-   Özellik `Name` türetilen sınıfta özelliğini gizler `Name` temel sınıf. Böyle bir durumda `new` değiştiricisi, türetilmiş sınıf içinde özellik bildirimi kullanılır:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Cast `(Employee)` temel sınıfta gizli özelliğine erişmek için kullanılır:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Gizleme üyeleri hakkında daha fazla bilgi için bkz. [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, iki sınıf `Cube` ve `Square`, soyut bir sınıf uygulama `Shape`ve onun soyut geçersiz kılma `Area` özelliği. Kullanımına dikkat edin [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi özellikleri. Program yan girdi olarak kabul eder ve kare ve küp alanlarını hesaplar. Ayrıca, alan bir giriş olarak kabul eder ve kare ve küp için karşılık gelen yan hesaplar.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
- [Otomatik Uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
