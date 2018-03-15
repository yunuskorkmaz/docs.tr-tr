---
title: "Özellikleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36345748e514f0e0a4c945d8ead149c7d8ca9a19
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="using-properties-c-programming-guide"></a>Özellikleri Kullanma (C# Programlama Kılavuzu)
Özellikler alanları ve yöntemleri yönlerini birleştirin. Bir nesne kullanıcıya bir özelliği bir alan görünüyor özelliği erişme aynı sözdizimini gerektirir. Bir sınıf uygulayan için temsil eden bir veya iki kod blokları bir özelliği olan bir [almak](../../../csharp/language-reference/keywords/get.md) erişimcisi ve/veya bir [ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimcisi. Kod bloğunu `get` erişimci özelliği okunduğunda yürütüldüğünde; kodu engellemek için `set` erişimci özelliği yeni bir değer atandığında yürütüldüğünde. Bir özelliği olmadan bir `set` erişimci salt okunur değerlendirilir. Bir özelliği olmadan bir `get` erişimci salt yazılır değerlendirilir. Her iki erişimciler sahip okuma-yazma özelliği değildir.  
  
 Alanlar özellikleri değişkenleri olarak sınıflandırılır değil. Bu nedenle, bir özellik olarak geçiremezsiniz bir [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi.  
  
 Özelliklere sahip çok sayıda kullanır: bir değişiklik; izin vermeden önce verileri doğrulayabilir Saydam veri burada verileri gerçekte bir veritabanı gibi diğer bazı kaynak alınır bir sınıfını kullanıma; bir olay oluşturma veya diğer alanlar değerinin değiştirilmesi gibi veri değiştirildiğinde, bunlar bir eylemde bulunabilir.  
  
 Özellikler alanı erişim düzeyini belirterek sınıfı bloğu içinde bildirilen, özelliğin türü izlemelidir, özellik adından ve bildiren bir kod bloğu tarafından izlenen bir `get`-erişimcisi ve/veya bir `set` erişimcisi. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Bu örnekte, `Month` bir özellik olarak, bu nedenle bildirilmiş `set` erişimcisi aşağıdakilerden emin olun `Month` değeri 1 ile 12 arasında ayarlanır. `Month` Özelliği, gerçek değer izlemek için özel bir alan kullanır. Bir özelliğin verilerin gerçek konumu genellikle özelliğin "yedekleme deposu olarak." adlandırılır Özel alanları yedekleme deposu olarak kullanmak üzere özellikleri için yaygın bir durumdur. Alan yalnızca özelliği çağırarak değiştirilebilir emin emin olmak için özel olarak işaretlenmiş. Ortak ve özel erişim kısıtlamaları hakkında daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Otomatik uygulanan özellikler basit özellik bildirimleri için basitleştirilmiş bir sözdizimi sağlar. Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Get erişimcisi  
 Gövdesini `get` erişimci, bir yöntemin benzer. Özellik türü değerini döndürmelidir. Yürütülmesi `get` erişimci alanın değerini okumaya eşdeğerdir. Örneğin, ne zaman iade özel değişkeninden `get` erişimci ve en iyi duruma getirme etkin, çağrısı `get` erişimci yöntemdir derleyici tarafından içermesinden; böylece yöntem çağrısı olmamasıdır. Ancak, bir sanal `get` derleyici derleme zamanında hangi yöntemi gerçekte çağrılabilir çalışma zamanında bilmediğinden erişimci yöntemi içermesinden olamaz. Aşağıda bir `get` bir özel alanın değerini döndürür erişimcisi `name`:  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Size özelliği dışında bir atama hedef olarak başvurduğunuzda `get` erişimci özelliğinin değerini okumaya çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 `get` Erişimci bitmelidir bir [dönmek](../../../csharp/language-reference/keywords/return.md) veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi ve denetim devre dışı erişimcisi gövde akışı olamaz.  
  
 Kullanarak nesnenin durumunu değiştirmek için hatalı bir programlama stili olan `get` erişimcisi. Örneğin, aşağıdaki erişimcisi yan etkisi, her nesnenin durumunu değiştirme üretir, `number` alan erişilir.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 `get` Erişimci alan değeri döndürür veya bu işlem ve döndürün için kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 Bir değere atamazsanız kesimdeki önceki kod, `Name` özelliği, onu döndürür değer gösterilir.  
  
## <a name="the-set-accessor"></a>Ayarlama erişimcisi  
 `set` Erişimci benzer dönüş türü olan bir yöntem [void](../../../csharp/language-reference/keywords/void.md). Adlı bir örtük parametresini kullanır `value`, özelliği türü, türü değil. Aşağıdaki örnekte, bir `set` erişimci eklenir `Name` özelliği:  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Özelliği için bir değer atadığınızda `set` erişimci, yeni değer sağlayan bağımsız değişken kullanarak çağrılır. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Örtük parametre adı kullanmak için bir hata olduğunu `value`, bir yerel değişken bildirimi için bir `set` erişimcisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Özellikler işaretlenir olarak `public`, `private`, `protected`, `internal`, `protected internal` veya `private protected`. Bu erişim değiştiricileri sınıfı kullanıcılarının özelliği nasıl erişebileceğiniz tanımlayın. `get` Ve `set` erişimciler aynı özellik için farklı erişim değiştiricileri sahip olabilir. Örneğin, `get` olabilir `public` salt okunur dışından erişim türü izin vermek ve `set` olabilir `private` veya `protected`. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir özellik kullanarak bir statik özellik olarak bildirilmelidir `static` anahtar sözcüğü. Sınıfının hiçbir örneği mevcut olsa bile bu özelliği arayanlara herhangi bir zamanda kullanılabilmesini sağlar. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir özellik kullanarak sanal bir özellik olarak işaretlenebilir [sanal](../../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü. Bu özellik davranışı kullanarak geçersiz kılmak türetilen sınıflar sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü. Bu seçenekler hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Sanal bir özelliği geçersiz kılınırken bir özellik de olabilir [korumalı](../../../csharp/language-reference/keywords/sealed.md), için türetilen sınıflar, artık sanal olduğunu belirten. Son olarak, bir özellik bildirilmedi [soyut](../../../csharp/language-reference/keywords/abstract.md). Bu sınıftaki uygulaması yoktur ve türetilen sınıflar, kendi uygulama yazmanız gerekir anlamına gelir. Bu seçenekler hakkında daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Kullanmak için bir hata olduğunu bir [sanal](../../../csharp/language-reference/keywords/virtual.md), [soyut](../../../csharp/language-reference/keywords/abstract.md), veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) erişimci Değiştirici bir [statik](../../../csharp/language-reference/keywords/static.md) özelliği.  
  
## <a name="example"></a>Örnek  
 Bu örnek örneği, statik ve salt okunur özellikleri gösterir. Klavye, artışlarla çalışan adını kabul eder `NumberOfEmployees` 1 ve görüntüler çalışan ad ve sayı.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, türetilen bir sınıfta aynı ada sahip başka bir özellik olarak gizli bir taban sınıftaki bir özelliğe erişmek gösterilmiştir.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Önceki örnekte önemli noktalar şunlardır:  
  
-   Özellik `Name` türetilen sınıfta özelliği gizler `Name` temel sınıf. Böyle bir durumda `new` değiştiricisi türetilmiş sınıf özelliğinde bildiriminde kullanılır:  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   Cast `(Employee)` temel sınıfı gizli özelliğinde erişmek için kullanılır:  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Gizleme üyeleri hakkında daha fazla bilgi için bkz: [new değiştiricisi](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, iki sınıf `Cube` ve `Square`, soyut bir sınıf uygulama `Shape`ve özetindeki geçersiz kılma `Area` özelliği. Kullanımına dikkat edin [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) özellikleri değiştiricisi. Program tarafı bir girdi olarak kabul eder ve kare ve küp için alanlar hesaplar. Ayrıca, alanda bir girdi olarak kabul eder ve karşılık gelen tarafı kare ve küp için hesaplar.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
 [Otomatik Uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
