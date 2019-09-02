---
title: Son değişiklikleri değerlendir-.NET Core
description: .NET Core 'un .NET sürümleri genelinde geliştiriciler için uyumluluğu sürdürme yolları hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: c68a19b8b98a98bb9c64f5b9fa60b378935e6e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2019
ms.locfileid: "67736564"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>.NET Core 'daki kırılmaya karşı değişiklikleri değerlendir

.NET, geçmişi boyunca sürümden sürüme ve .NET 'in özellikleri arasında yüksek düzeyde uyumluluk tutmaya çalıştı. Bu, .NET Core için doğru olmaya devam eder. .NET Core, .NET Framework bağımsız olan yeni bir teknoloji olarak düşünülebilir, ancak iki ana etken .NET Core 'un .NET Framework arasında sınırsız olmasına izin verebilir:

- Asıl olarak çok sayıda geliştirici geliştirmiş veya .NET Framework uygulamaları geliştirmeye devam eder. .NET uygulamalarında tutarlı davranış beklentilerine sahip olurlar.

- .NET Standard kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API 'Leri hedefleyen kitaplıklar oluşturmalarına olanak tanır. Geliştiriciler .NET Core uygulamasında kullanılan bir kitaplığın, .NET Framework uygulamasında kullanılan aynı kitaplıkla aynı şekilde davranmasını bekler.

Geliştiriciler .NET uygulamaları genelinde uyumlulukla birlikte .NET Core sürümleri arasında yüksek düzeyde uyumluluk bekler. Özellikle .NET Core 'un önceki bir sürümü için yazılan kod, daha sonraki bir .NET Core sürümünde sorunsuz çalışmalıdır. Aslında birçok geliştirici, .NET Core 'un yeni yayımlanmış sürümlerinde bulunan yeni API 'Lerin, bu API 'Lerin tanıtıldıkları yayın öncesi sürümlerle de uyumlu olmasını bekler.

Bu makalede, uyumluluk değişikliklerinin (veya son değişikliklerin) kategorileri ve .NET ekibinin bu kategorilerin her birinde değişiklikleri değerlendirme yöntemi özetlenmektedir. .NET ekibinin olası önemli değişikliklere nasıl yaklaşılacağını anlamak, var olan API 'lerin davranışını değiştiren [DotNet/corefx](https://github.com/dotnet/corefx) GitHub deposundaki çekme isteklerini açan geliştiriciler için özellikle yararlıdır.

> [!NOTE]
> İkili uyumluluk ve geri uyumluluk gibi uyumluluk kategorilerinin bir tanımı için bkz. [değişiklik kategorilerini bölme](categories.md).

Aşağıdaki bölümlerde .NET Core API 'Lerinde yapılan değişiklik kategorileri ve bunların uygulama uyumluluğuyla ilgili kategoriler açıklanmaktadır. ✔️ simgesi, belirli bir değişiklik türüne izin verildiğini gösterir, ❌ izin verilmediğini gösterir ve ❓ izin verilmeyen bir değişikliği gösterir. Bu son kategorideki değişiklikler, önceden tahmin edilebilir, belirgin ve tutarlı bir önceki davranışın nasıl olduğunu değerlendirmenizi gerektirir.

> [!NOTE]
> .NET Core kitaplıklarının değişikliklerinin nasıl değerlendirildiğini gösteren bir kılavuz olarak sunabilmesinin yanı sıra, kitaplık geliştiricileri birden çok .NET uygulaması ve sürümünü hedefleyen kitaplıklarında yapılan değişiklikleri değerlendirmek için de bu ölçütleri kullanabilir.

## <a name="modifications-to-the-public-contract"></a>Ortak Sözleşmede yapılan değişiklikler

Bu kategorideki değişiklikler bir türün genel yüzey alanını *değiştirir* . Bu kategorideki değişikliklerden büyük bir olasılıkla, *geriye dönük uyumluluğu* ihlal etdiklerinden (API 'nin önceki bir sürümü ile geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütülmesi için geliştirilmiş bir uygulama özelliği) izin verilmez.

### <a name="types"></a>Türler

- **arabirim bir temel tür tarafından zaten uygulandığında bir türden arabirim uygulamasını kaldırma ✔️**

- **Türe yeni bir arabirim uygulamasını ekleme ❓**

  Bu, mevcut istemcileri olumsuz etkilemediğinden, kabul edilebilir bir değişiklik. Yeni uygulamanın kabul edilebilir olarak kalması için, bu türdeki tüm değişiklikler burada tanımlanan kabul edilebilir değişiklik sınırları içinde çalışmalıdır. Bir tasarımcının veya seri hale getiricinin alt düzey tüketilemeyecek kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklenirken aşırı dikkatli olmanız gerekir. <xref:System.Runtime.Serialization.ISerializable> Arabirim bir örnektir.

- **Yeni bir temel sınıfa giriş ❓**

  Bir tür, yeni bir [soyut](../../csharp/language-reference/keywords/abstract.md) üye sunmaz veya var olan türlerin semantiğini ya da davranışını değiştirmek değilse, mevcut iki tür arasında bir hiyerarşiye tanıtılamaz. Örneğin, .NET Framework 2,0 ' de, <xref:System.Data.Common.DbConnection> sınıfı daha önce doğrudan öğesinden <xref:System.ComponentModel.Component>türetilmiş olan için <xref:System.Data.SqlClient.SqlConnection>yeni bir temel sınıf haline geldi.

- **bir türü bir derlemeden diğerine taşımak ✔️**

  *Eski* derlemenin yeni derlemeye işaret <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> eden ile işaretlenmiş olması gerektiğini unutmayın.

- **✔️ [Yapı](../../csharp/language-reference/keywords/struct.md) türünü bir `readonly struct` türe değiştirme**

  Türe bir tür değiştirme `readonly struct` `struct` yapılmasına izin verilmediğini unutmayın.
  
- ***erişilebilir* (genel veya korumalı) oluşturucular olmadığında bir türe [Sealed](../../csharp/language-reference/keywords/sealed.md) veya [abstract](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü eklemek ✔️**

- **bir türün görünürlüğünü genişletmek ✔️**

- **Bir türün ad alanını veya adını değiştirme ❌**

- **Ortak bir türü yeniden adlandırma veya kaldırma ❌**

   Bu, yeniden adlandırılan veya kaldırılan türü kullanan tüm kodları keser.

- **Sabit listesinin temel alınan türünü değiştirme ❌**

   Bu bir derleme zamanı ve davranışsız değişiklik ve öznitelik bağımsız değişkenlerini ayrıştırılabilir hale getirmek için ikili bir değişiklik de yapar.

- **Daha önce korumasız bir tür ❌ mühürlü**

- **Bir arabirimin temel türleri kümesine arabirim ekleme ❌**

   Bir arabirim daha önce uygulanmayan bir arabirim uygularsa, arabirimin orijinal sürümünü uygulayan tüm türler bozulur.

- **Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırmak ❓**

  Arabirim kaldırma kuralı için bir özel durum vardır: kaldırılan arabirimden türetilen bir arabirimin uygulamasını ekleyebilirsiniz. Örneğin, türü veya arabirimi <xref:System.IDisposable> <xref:System.ComponentModel.IComponent>' nin <xref:System.IDisposable>uyguladığı bir şekilde, öğesini kaldırabilirsiniz.

- **Bir `readonly struct` türü [Yapı](../../csharp/language-reference/keywords/struct.md) türüne değiştirme ❌**

  Türe bir tür değişikliğine `struct` `readonly struct` izin verildiğini unutmayın.

- **[Yapı](../../csharp/language-reference/keywords/struct.md) türünü `ref struct` tür olarak değiştirme ❌ ve tam tersi**

- **Bir türün görünürlüğünü azaltma ❌**

   Ancak, bir türün görünürlüğünü artırmak için izin verilir.

### <a name="members"></a>Üyeler

- **[sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletmek ✔️**

- ***erişilebilir* (genel veya korumalı) oluşturuculara sahip olmayan veya tür [korumalı](../../csharp/language-reference/keywords/sealed.md) olan bir ortak türe soyut üye ekleme ✔️**

  Ancak, erişilebilir (genel veya korumalı) oluşturuculara `sealed` sahip bir türe soyut üye eklenmesine izin verilmez.

- **tür erişilebilir (genel veya korumalı) oluşturuculara sahip olmadığında veya tür [mühürleniyorsa](../../csharp/language-reference/keywords/sealed.md) [korunan](../../csharp/language-reference/keywords/protected.md) üyenin görünürlüğünü kısıtlama ✔️**

- **bir üyeyi hiyerarşide daha yüksek bir sınıfa, onun kaldırıldığı türden daha yukarıya taşımak ✔️**

- **geçersiz kılma ekleme veya kaldırma ✔️**

  Bir geçersiz kılma ile tanışın, önceki tüketicilerin [taban](../../csharp/language-reference/keywords/base.md)çağrılırken geçersiz kılma üzerinde atlama yapılmasına neden olabilir.

- **sınıfın daha önce Oluşturucusu yoksa, bir sınıfa bir Oluşturucu eklemek ✔️ varsayılan (parametresiz) bir Oluşturucu ile birlikte**

   Ancak, parametresiz oluşturucuyu eklemeden daha önceden hiç oluşturucuya sahip olmayan bir sınıfa bir Oluşturucu eklemeye izin verilmez.

- **üyeyi [abstract](../../csharp/language-reference/keywords/abstract.md) 'ten [sanal](../../csharp/language-reference/keywords/virtual.md) 'e değiştirme ✔️**

- **`ref readonly` bir`ref` dönüş değerine değiştirme ✔️ (sanal yöntemler veya arabirimler dışında)**

- **alanın statik türü kesilebilir değer türünde değilse, bir alandan [ReadOnly](../../csharp/language-reference/keywords/readonly.md) öğesini kaldırma ✔️**

- **daha önce tanımlanmayan yeni bir olayı çağırmak ✔️**

- **Türe yeni bir örnek alanı ekleme ❓**

   Bu değişiklik Serileştirmeyi etkiler.

- **Ortak üye veya parametreyi yeniden adlandırma veya kaldırma ❌**

   Bu, yeniden adlandırılan veya kaldırılan üyeyi veya parametreyi kullanan tüm kodları keser.

   Bunun yanı sıra, bir alıcı veya ayarlayıcının bir özellikten kaldırılmasını veya yeniden adlandırılmasını, ayrıca sabit listesi üyelerini yeniden adlandırmayı veya kaldırmayı da içerdiğini unutmayın.

- **Arabirime üye ekleme ❌**

- **Ortak bir sabit veya numaralandırma üyesinin değerini değiştirme ❌**

- **Bir özelliğin, alanın, parametrenin veya dönüş değerinin türünü değiştirme ❌**

- **Parametre sırasını ekleme, kaldırma veya değiştirme ❌**

- **Bir parametreden [ın](../../csharp/language-reference/keywords/in.md), [Out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğünü ekleme veya kaldırma ❌**

- **Bir parametreyi yeniden adlandırma ❌ (büyük/küçük harf durumunu değiştirme dahil)**

  Bunun iki nedenden dolayı bölünmesi kabul edilir:
  
  - Visual Basic ve [dinamik](../../csharp/language-reference/keywords/dynamic.md) sürümünde geç bağlama özelliği gibi geç bağlantılı senaryoları keser C#.
  
  - Geliştiriciler [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandıklarında [kaynak uyumluluğunu](categories.md#source-compatibility) keser.

- **`ref` Dönüş değerinden`ref readonly` dönüş değerine değiştirme ❌**

- **bir sanal yöntem veya `ref readonly` arabirimdeki bir `ref` dönüş değerine değiştirme ❌️**

- **Üyelerden [Özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma ❌**

- **Bir üyenin [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü kaldırma ❌**

  Derleyici, sanal olmayan yöntemleri çağırmak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) ara dil (IL) yönergelerini yayma eğilimidir (`callvirt` bir null denetimi gerçekleştirir, normal çağrı olmadığında), bu davranış C# Bazı nedenlerle ınvariable:
  - C#, .NET 'in hedeflediği tek dil değildir.
  
  - C# Derleyici, hedef yöntem sanal olmayan `callvirt` ve muhtemelen null olmayan ( [?. null yayma operatörü](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıyı en iyi hale getirmeye çalışır.
  
  Bir yöntem sanal hale getirmek, tüketici kodunun genellikle neredeyse bir kez çağrılmasını sona erdirmek anlamına gelir.

- **Bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcük eklemek ❌**

- **Bir sanal üyeyi soyut hale getirmek ❌**

  Bir [sanal üye](../../csharp/language-reference/keywords/virtual.md) , türetilmiş bir sınıf tarafından geçersiz kılınabilen bir yöntem uygulamasını sağlar. [Soyut üye](../../csharp/language-reference/keywords/abstract.md) , uygulama sağlamaz ve geçersiz *kılınmalıdır* .

- **Erişilebilir (genel veya korumalı) oluşturuculara sahip ve [korumalı](../../csharp/language-reference/keywords/sealed.md) olmayan bir ortak türe soyut üye ekleme ❌**

- **Üyenin [statik](../../csharp/language-reference/keywords/static.md) anahtar sözcüğünü ekleme veya kaldırma ❌**

- **Var olan bir aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan bir aşırı yükleme eklemek ❌**

  Bu, önceki aşırı yüklemeye bağlanan mevcut istemcileri keser. Örneğin, bir sınıfın bir <xref:System.UInt32>yöntemi kabul eden tek bir sürümü varsa, var olan bir tüketici bir <xref:System.Int32> değer geçirirken bu aşırı yüklemeye başarıyla bağlanır. Ancak, kabul eden bir <xref:System.Int32>aşırı yükleme eklerseniz veya geç bağlamayı kullandığınızda, derleyici artık yeni aşırı yüklemeye bağlanır. Farklı davranış sonuç alıyorsa, bu durum bir son değişiklik olur.

- **Parametresiz oluşturucuyu eklemeden daha önce Oluşturucusu olmayan bir sınıfa Oluşturucu Ekleme ❌**

- **bir alana [ReadOnly](../../csharp/language-reference/keywords/readonly.md) eklemek ❌️**

- **Üyenin görünürlüğünü azaltma ❌**

   Bu, *erişilebilir* (ortak veya korumalı) oluşturucular olduğunda [korumalı](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü azaltmak ve tür [Sealed](../../csharp/language-reference/keywords/sealed.md) *değilse* içerir. Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.

   Üyenin görünürlüğünü arttırmaya izin verildiğini unutmayın.

- **Üyenin türünü değiştirme ❌**

   Bir metodun veya bir özelliğin ya da alanın dönüş değeri değiştirilemez. Örneğin, döndüren <xref:System.Object> bir yöntemin imzası, bir <xref:System.String>veya döndürmek için değiştirilemez.

- **Daha önce durumu olmayan bir yapıya alan ekleme ❌**

  Kesin atama kuralları, değişken türü durum bilgisi olmayan bir yapı olduğu sürece başlatılmamış değişkenlerin kullanılmasına izin verir. Yapı durum bilgisi olarak yapılırsa, kod başlatılmamış verilerle bitebilecek. Bu, büyük olasılıkla kaynak bölünmesi ve ikili bir değişiklik değişikliği olur.

- **Daha önce hiç tetiklendiğinde var olan bir olayı ❌ tetiklenme**

## <a name="behavioral-changes"></a>Davranış değişiklikleri

### <a name="assemblies"></a>Bütünleştirilmiş kodlar

- **aynı platformlar hala desteklenmeden bir derlemeyi taşınabilir hale getirmek ✔️**

- **Bir derlemenin adını değiştirme ❌**
- **Bir derlemenin ortak anahtarını değiştirme ❌**

### <a name="properties-fields-parameters-and-return-values"></a>Özellikler, alanlar, parametreler ve dönüş değerleri

- **bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme ✔️**

  Örneğin, bir türü <xref:System.Object> döndüren bir yöntem bir <xref:System.String> örnek döndürebilir. (Ancak, yöntem imzası değiştirilemez.)

- **üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse bir özellik veya parametre için kabul edilen değerlerin aralığını ✔️ artırma**

  Yönteme geçirilebilecek veya üye tarafından döndürülen değer aralığı genişken, parametre veya üye türü ' nin genişleyebilir olduğunu unutmayın. Örneğin, bir yönteme geçirilen değerler 0-124 ' den 0-255 ' e genişleyebilir, parametre türü ' dan <xref:System.Byte> <xref:System.Int32>' a geçiş yapılamaz.

- **Üye [sanal](../../csharp/language-reference/keywords/virtual.md) ise, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma ❌**

   Bu değişiklik, genişletilmiş değer aralığı için doğru şekilde çalışmayacak olan geçersiz kılınan üyeleri keser.

- **Bir özellik veya parametre için kabul edilen değerlerin aralığını ❌ azaltma**

- **Bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma ❌**

- **Bir özellik, alan, yöntem dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerleri değiştirme ❌**

- **Bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme ❌**

- **Sayısal bir dönüş değerinin hassasiyetini değiştirme ❌**

- **Girişi ayrıştırırken bir değişikliği ❓ ve yeni özel durumlar oluşturma (belgede ayrıştırma davranışı belirtilmese de)**

### <a name="exceptions"></a>Özel Durumlar

- **✔️ Mevcut bir özel durumdan daha fazla türetilmiş özel durum atma**

  Yeni özel durum var olan bir özel durumun alt sınıfı olduğundan, önceki özel durum işleme kodu özel durumu işlemeye devam eder. Örneğin, .NET Framework 4 ' te kültür oluşturma ve alma yöntemleri kültür bulunamazsa bir yerine <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> bir oluşturmaya başlamıştır. <xref:System.Globalization.CultureNotFoundException> Öğesinden<xref:System.ArgumentException>türetildiğinden, bu kabul edilebilir bir değişiklik.

- **daha özel bir özel durum <xref:System.NotSupportedException> <xref:System.NotImplementedException>oluşturan ✔️,,<xref:System.NullReferenceException>**

- **kurtarılamaz olarak kabul edilen bir özel durum ✔️**

  Kurtarılamaz özel durumlar yakalanmamalıdır, bunun yerine üst düzey bir catch-all işleyicisi tarafından işlenmelidir. Bu nedenle, kullanıcıların bu açık özel durumları yakalayan kodun olması beklenmez. Kurtarılamaz özel durumlar şunlardır:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **Yeni bir kod yolunda yeni bir özel durum oluşturma ✔️**

  Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen mevcut kodla yürütülemeyen yeni bir kod yolu için geçerli olmalıdır.

- **daha sağlam davranışı veya yeni senaryoları etkinleştirmek için bir özel durumu kaldırma ✔️**

  Örneğin, daha önce `Divide` yalnızca pozitif değerleri işlenmiş ve başka bir <xref:System.ArgumentOutOfRangeException> şekilde oluşturulmuş bir yöntem, özel durum oluşturmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.

- **bir hata iletisinin metnini değiştirme ✔️**

  Geliştiriciler, kullanıcının kültürüne göre de değişen hata iletilerinin metnine güvenmemelidir.

- **Yukarıda listelenmeyen başka bir durumda özel durum ❌ oluşturma**

- **Yukarıda listelenmeyen başka bir durumda özel durumu kaldırmak ❌**

### <a name="attributes"></a>Öznitelikler

- **✔️, observable *olmayan* bir özniteliğin değerini değiştirme**

- **Observable olan bir özniteliğin değerini değiştirme ❌**

- **Özniteliği kaldırma ❓**

  Çoğu durumda, bir özniteliği ( <xref:System.NonSerializedAttribute>gibi) kaldırmak, önemli bir değişiklik olur.

## <a name="platform-support"></a>Platform desteği

- **daha önce desteklenmeyen bir platformda bir işlemi desteklemek ✔️**

- **❌, Bir platformda daha önce desteklenen bir işlem için belirli bir hizmet paketini desteklememe veya bu aşamada gerektirme**

## <a name="internal-implementation-changes"></a>İç uygulama değişiklikleri

- **İç türün yüzey alanını değiştirme ❓**

   Bu tür değişikliklere genel olarak izin verilir, ancak özel yansımayı keser. Bazı durumlarda, popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin iç API 'Lere bağlı olduğu durumlarda, bu değişikliklere izin verilmiyor olabilir.

- **Üyenin iç uygulamasını değiştirme ❓**

  Bu değişikliklere genel olarak izin verilir, ancak özel yansımayı keser. Bazı durumlarda, müşteri kodunun genellikle özel yansımaya bağlı olması veya değişikliğin istenmeyen yan etkileri sağlaması durumunda bu değişikliklere izin verilmiyor olabilir.

- **✔️ bir işlemin performansını artırma**

   Bir işlemin performansını değiştirme yeteneği zorunludur, ancak bu tür değişiklikler bir işlemin geçerli hızına bağlı kodu kesebilir. Bu, özellikle de zaman uyumsuz işlemlerin zamanlamasına bağlı olan kodun bir doğrudur. Performans değişikliğinin, söz konusu API 'nin diğer davranışları üzerinde hiçbir etkisi olmaması gerektiğini unutmayın; Aksi takdirde, değişiklik koparacaktır.

- **bir işlemin performansını dolaylı olarak değiştirme (ve genellikle olumsuz yönde) ✔️**

  Söz konusu değişiklik başka bir nedenden dolayı bölme olarak kategorilere ayrılmazsa, bu kabul edilebilir. Genellikle, ek işlemleri içerebilen veya yeni işlevsellik ekleyen eylemlerin alınması gerekir. Bu, neredeyse her zaman performansı etkiler ancak API 'yi soru işlevinin beklendiği gibi yapmak için gerekli olabilir.

- **Zaman uyumlu bir API 'yi zaman uyumsuz olarak değiştirme ❌ (ve tam tersi)**

## <a name="code-changes"></a>Kod değişiklikleri

- **parametreye [params](../../csharp/language-reference/keywords/params.md) ekleme ✔️**

- **Bir [yapıyı](../../csharp/language-reference/keywords/struct.md) bir [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ❌ ve tam tersi**

- **Bir kod bloğuna [Checked](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü ekleme ❌**

   Bu değişiklik, daha önce bir <xref:System.OverflowException> ve oluşturması için yürütülen kodun kabul edilemez olmasını sağlayabilir.

- **Parametreleri bir [](../../csharp/language-reference/keywords/params.md) parametreden kaldırmak ❌**

- **Olayların tetiklenme sırasını değiştirme ❌**

  Geliştiriciler, olayların aynı sırayla tetiklenmesi makul bir şekilde bekleyebilir ve geliştirici kodu genellikle olayların tetikleneceği sıraya bağlıdır.

- **Belirli bir eylemde bir olayın bir kısmını kaldırma ❌**

- **❌ Olayların kaç kez çağrıldığını değiştirme**

- **❌ Bir numaralandırma <xref:System.FlagsAttribute> türüne ekleme**
