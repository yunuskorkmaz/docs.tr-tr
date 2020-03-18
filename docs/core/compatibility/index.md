---
title: Kesme değişiklik türleri
description: .NET Core'un .NET sürümlerinde geliştiriciler için uyumluluğu nasıl korumaya çalıştığı ve ne tür bir değişikliğin kırılma sı olarak kabul edilir.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628598"
---
# <a name="changes-that-affect-compatibility"></a>Uyumluluğu etkileyen değişiklikler

.NET, geçmişi boyunca sürümden sürüme ve .NET'in tatları arasında yüksek düzeyde uyumluluk sağlama girişiminde bulundu. Bu ,NET Core için doğru olmaya devam ediyor. .NET Core,.NET Framework'den bağımsız yeni bir teknoloji olarak kabul edilse de, .NET Core'un .NET Framework'den sapma yeteneğini iki ana faktör sınırlayabilirsiniz:

- Çok sayıda geliştirici başlangıçta geliştirmiştir veya .NET Framework uygulamalarını geliştirmeye devam eder. .NET uygulamaları arasında tutarlı davranış beklerler.

- .NET Standart kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API'leri hedefleyen kitaplıklar oluşturmasına olanak tanır. Geliştiriciler, .NET Core uygulamasında kullanılan bir kitaplığın .NET Framework uygulamasında kullanılan kitaplığın aynı şekilde olmasını bekler.

.NET uygulamalarında uyumlulukla birlikte, geliştiriciler .NET Core sürümlerinde yüksek düzeyde uyumluluk beklerler. Özellikle, .NET Core'un önceki bir sürümü için yazılan kod, .NET Core'un sonraki bir sürümünde sorunsuz bir şekilde çalıştırılmalıdır. Aslında, birçok geliştirici .NET Core'un yeni yayımlanan sürümlerinde bulunan yeni API'lerin, bu API'lerin sunulduğu ön sürüm sürümleriyle de uyumlu olmasını bekleyilmiştir.

Bu makalede, uyumluluk değişiklikleri (veya kesme değişiklikleri) kategorileri ve .NET ekibinin bu kategorilerin her birinde değişiklikleri değerlendirme şekli özetlendi. .NET ekibinin olası kesme değişikliklerine nasıl yaklaştığını anlamak, özellikle varolan API'lerin davranışını değiştiren [dotnet/runtime](https://github.com/dotnet/runtime) GitHub deposunda çekme isteklerini açan geliştiriciler için yararlıdır.

> [!NOTE]
> İkili uyumluluk ve geriye dönük uyumluluk gibi uyumluluk kategorilerinin tanımı [için](categories.md)bkz.

Aşağıdaki bölümlerde .NET Core API'lerinde yapılan değişikliklerin kategorileri ve bunların uygulama uyumluluğu üzerindeki etkileri açıklanır. Değişikliklere ✔️ izin verilir, ❌izin verilmez veya önceki davranışın ne kadar öngörülebilir, açık ve tutarlı bir şekilde ❓ bir yargı ve değerlendirme gerektirir.

> [!NOTE]
> .NET Core kitaplıklarındaki değişikliklerin nasıl değerlendirildiği konusunda bir rehber olarak hizmet vermenin yanı sıra, kitaplık geliştiricileri bu ölçütleri birden çok .NET uygulamasını ve sürümlerini hedefleyen kitaplıklarındaki değişiklikleri değerlendirmek için de kullanabilir.

## <a name="modifications-to-the-public-contract"></a>Kamu sözleşmesinde yapılan değişiklikler

Bu kategorideki değişiklikler, bir türün ortak yüzey alanını değiştirir. Geriye *dönük uyumluluğu* ihlal ettikleri için bu kategorideki değişikliklerin çoğuna izin verilmez (bir API'nin önceki sürümüyle geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütebilme yeteneği).

### <a name="types"></a>Türler

- ✔️ **Izin verilir: Arabirim zaten bir temel türü tarafından uygulandığında bir türden arabirim uygulamasını kaldırma**

- ❓ **YARGI GEREKTIRIR: Bir türe yeni bir arayüz uygulaması ekleme**

  Varolan istemcileri olumsuz etkilemediği için bu kabul edilebilir bir değişikliktir. Türdeki herhangi bir değişikliğin, yeni uygulamanın kabul edilebilir kalması için burada tanımlanan kabul edilebilir değişikliklerin sınırları içinde çalışması gerekir. Bir tasarımcının veya seri göstericinin alt düzey tüketilemeyen kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklerken çok dikkatli olunması gerekir. Bir örnek <xref:System.Runtime.Serialization.ISerializable> arayüzdür.

- ❓ **YARGI GEREKTIRIR: Yeni bir taban sınıf tanıtılması**

  Bir tür, yeni [soyut](../../csharp/language-reference/keywords/abstract.md) üyeler tanımazsa veya varolan türlerin anlamlarını veya davranışını değiştirmiyorsa, varolan iki tür arasında bir hiyerarşiye dönüştürülebilir. Örneğin, .NET Framework 2.0'da <xref:System.Data.Common.DbConnection> <xref:System.Data.SqlClient.SqlConnection>sınıf, daha önce doğrudan .'den <xref:System.ComponentModel.Component>türetilmiş olan yeni bir taban sınıf haline geldi.

- **✔️ Izin verilir: Bir türbir derlemeden diğerine taşıma**

  *Eski* derleme, yeni derlemeye işaret eden <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> noktalarla işaretlenmelidir.

- ✔️ **Izin VERILIR: [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü `readonly struct` bir türe değiştirme**

  Bir `readonly struct` türü bir `struct` türle değiştirmek yasaktır.

- ✔️ **İzİn VERİlMESİ: *Erişilebilir* (ortak veya korumalı) yapıcılar olmadığında bir türe [mühürlü](../../csharp/language-reference/keywords/sealed.md) veya [soyut](../../csharp/language-reference/keywords/abstract.md) anahtar kelime ekleme**

- ✔️ **IZIN VERİlDİ: Bir türün görünürlüğünü genişletme**

- ❌**ADVERİl: Bir türün ad alanını veya adını değiştirme**

- ❌**ADVERİl: Genel bir türü yeniden adlandırma veya kaldırma**

   Bu, yeniden adlandırılmış veya kaldırılan türü kullanan tüm kodu kırar.

- ❌**İzin VERİlMEMİş: Bir numaralandırmanın altında yatan türü değiştirme**

   Bu derleme zamanı ve davranışsal kırılma değişikliğinin yanı sıra öznitelik bağımsız değişkenlerini ayrıştırılamaz hale getirebilecek ikili bir kırılma değişikliğidir.

- ❌**İzİn VERİlMEMİş: Daha önce mühürlenmemiş bir tür mühürleme**

- ❌**İzin VERİlMEMİş: Bir arabirimin temel türleri kümesine arabirim ekleme**

   Bir arabirim daha önce uygulamadığı bir arabirim uygularsa, arabirimin özgün sürümünü uygulayan tüm türler bozulur.

- ❓ **YARGI GEREKTIRIR: Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırma**

  Arabirim kaldırma kuralının bir istisnası vardır: kaldırılan arabirimden türeyen bir arabirim uygulamasını ekleyebilirsiniz. Örneğin, tür veya <xref:System.IDisposable> arabirim şimdi uygular <xref:System.ComponentModel.IComponent>, hangi <xref:System.IDisposable>uygular kaldırabilirsiniz.

- ❌**İzin VERİlMEMİş: Bir `readonly struct` türbirin [yapı](../../csharp/language-reference/builtin-types/struct.md) türüne değiştirilmesi**

  Ancak, bir `struct` türün `readonly struct` bir türe değiştirilmesine izin verilir.

- ❌**İzin VERİlMEMİş: [Bir](../../csharp/language-reference/builtin-types/struct.md) yapı `ref struct` türünü bir türe değiştirme ve bunun tersi**

- ❌**İzin VERİlMEMİş: Bir türün görünürlüğünü azaltmak**

   Ancak, bir türün görünürlüğünü artırmak için izin verilir.

### <a name="members"></a>Üyeler

- ✔️ **Izin: [Sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletme**

- ✔️ **Izin: *Erişilebilir* (ortak veya korumalı) oluşturucusu olmayan veya türü [mühürlü](../../csharp/language-reference/keywords/sealed.md) olan genel bir türe soyut bir üye ekleme**

  Ancak, erişilebilir (ortak veya korumalı) oluşturuculara sahip ve izin `sealed` verilmeyen bir türe soyut bir üye eklemek.

- **✔️ Izin: Türü erişilebilir (ortak veya korumalı) yapıcılar olmadığında veya türü [mühürlendiğinde](../../csharp/language-reference/keywords/sealed.md) [korunan](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü kısıtlama**

- **✔️ İzin ver: Bir üyeyi hiyerarşide kaldırıldığı türden daha yüksek bir sınıfa taşıma**

- **✔️ İzNEdİlİr: Bir geçersiz kılma ekleme veya kaldırma**

  Geçersiz kılmanın tanıtılması, önceki tüketicilerin [tabanı](../../csharp/language-reference/keywords/base.md)ararken geçersiz kılmayı atlayabına neden olabilir.

- **✔️ İzİn VERİlMeSİ: Sınıfın daha önce oluşturucusu yoksa parametresiz bir yapıcı ile birlikte bir sınıfa yapıcı ekleme**

   Ancak, parametresiz oluşturucu *eklemeden* daha önce hiçbir oluşturucusu olan bir sınıfa bir oluşturucu eklenmesine izin verilmez.

- **✔️ Izin: Bir üyeyi [soyuttan](../../csharp/language-reference/keywords/abstract.md) [sanala](../../csharp/language-reference/keywords/virtual.md) değiştirme**

- **✔️ Izin: `ref readonly` A'dan `ref` dönüş değerine değiştirme (sanal yöntemler veya arabirimler hariç)**

- ✔️ **Izin verilmeyen: Alanın statik türü mutable değer türü olmadığı sürece, [yalnızca](../../csharp/language-reference/keywords/readonly.md) bir alandan okuma kaldırma**

- ✔️ **Izin verildi: Daha önce tanımlanmamış yeni bir olayı çağırma**

- ❓ **YARGI GEREKTIRIR: Bir türe yeni bir örnek alanı ekleme**

   Bu değişiklik serileştirmeyi etkiler.

- ❌**ADİZ: Bir kamu üyesinin veya parametrenin yeniden adlandırılması veya kaldırılması**

   Bu, yeniden adlandırılmış veya kaldırılan üyeyi veya parametreyi kullanan tüm kodu kırar.

   Bu, bir özellikten bir vericiyi veya ayarlayıcıyı kaldırmayı veya yeniden adlandırmayı ve numaralandırma üyelerini yeniden adlandırmayı veya kaldırmayı içerir.

- ❌**İzin VERİlMESİn: Arabirime üye ekleme**

- ❌**İzin VERİlMEMİş: Genel sabit veya numaralandırma üyesinin değerini değiştirme**

- ❌**İzin VERİlMEMİş: Bir özelliğin, alanın, parametrenin veya geri dönüş değerinin türünü değiştirme**

- ❌**İzin VERİlMEMİş: Parametrelerin sırasını ekleme, kaldırma veya değiştirme**

- ❌**İzin VERİlMEMİş: [Bir](../../csharp/language-reference/keywords/in.md)parametreden in , [out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğü ekleme veya kaldırma**

- ❌**ADVERİl: Bir parametreyi yeniden adlandırma (servis talebinin değiştirilmesi dahil)**

  Bu iki nedenden dolayı kırma olarak kabul edilir:

  - Visual Basic'te geç bağlama özelliği ve C#'da [dinamik](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) gibi geç giden senaryoları kırar.

  - Geliştiriciler [adlandırılmış bağımsız değişkenleri](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandığında [kaynak uyumluluğunu](categories.md#source-compatibility) bozar.

- ❌**İzin VERİlMEMİş: `ref` İade `ref readonly` değerinden geri dönüş değerine değiştirme**

- ❌️**İzin VERİlMEMİş: Sanal bir yöntem veya arabirimde a'dan `ref readonly` `ref` geri dönüş değerine değiştirme**

- ❌**İzİn VERİlMESİ: Bir üyeden [özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma**

- ❌**İzin VERİlMESİn: [Sanal](../../csharp/language-reference/keywords/virtual.md) anahtar kelimeyi üyeden kaldırma**

  C# derleyicisi sanal olmayan yöntemleri aramak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) yönergeleri yağlama eğilimindedir`callvirt` çünkü bu genellikle bir kırılma değişiklik olmasa da (normal bir arama yok, null denetim gerçekleştirir), bu davranış çeşitli nedenlerle değişmez değildir:
  - C# .NET'in hedef lemesi tek dil değildir.

  - C# derleyicisi, `callvirt` hedef yöntem sanal olmadığında ve büyük olasılıkla null olmadığında [(?. null yayılma işleci](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıya giderek daha fazla optimizasyon yapmaya çalışır.

  Bir yöntemi sanal hale getirmek, tüketici kodunun genellikle onu sanal olmayan olarak adlandırması anlamına gelir.

- ❌**İzin VERİlMESİn: Bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar kelime ekleme**

- ❌**DISALLOWED: Sanal üye soyut yapma**

  [Sanal üye,](../../csharp/language-reference/keywords/virtual.md) türetilmiş bir sınıf tarafından geçersiz *kılınabilecek* bir yöntem uygulaması sağlar. Soyut bir [üye](../../csharp/language-reference/keywords/abstract.md) hiçbir uygulama sağlar ve geçersiz *kılınmalıdır.*

- ❌**İzin VERİlMEMİş: Erişilebilir (ortak veya korumalı) oluşturuculara sahip ve [mühürlü](../../csharp/language-reference/keywords/sealed.md) olmayan bir genel türe soyut bir üye ekleme**

- ❌**İZIN VERİlMESİn: [Statik](../../csharp/language-reference/keywords/static.md) anahtar kelimenin üyeden eklenmesi veya kaldırılması**

- ❌**İzİn VERİlMESİ: Varolan aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan** aşırı yük ekleme

  Bu, önceki aşırı yüklemeye bağlı varolan istemcileri kırar. Örneğin, bir sınıfın bir <xref:System.UInt32>yöntemi kabul eden tek bir sürümü varsa, varolan bir tüketici bir <xref:System.Int32> değeri geçerken bu aşırı yüke başarıyla bağlanır. Ancak, yeniden derleme veya geç bağlama <xref:System.Int32>kullanırken bir , kabul eden bir aşırı yük eklerseniz, derleyici şimdi yeni aşırı yüke bağlanır. Farklı davranış sonuçları, bu bir kırılma değişikliğidir.

- ❌**İzİn VERİlMEMİş: Parametresiz oluşturucueklemeden daha önce oluşturucu olmayan bir sınıfa yapıcı ekleme**

- ❌️**İzİn VERİlMESİn: [Yalnızca](../../csharp/language-reference/keywords/readonly.md) bir alana okuma ekleme**

- ❌**İzİn VERİlMESİ: Bir üyenin görünürlüğünü azaltmak**

   Bu, *erişilebilir* `public` ( veya `protected`) oluşturucular olduğunda ve türü [mühürlü](../../csharp/language-reference/keywords/sealed.md) *olmadığında* [korunan](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü azaltmayı içerir. Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.

   Bir üyenin görünürlüğünün artırılmasına izin verilir.

- ❌**İzin VERİlMEMİş: Üye nin türünü değiştirme**

   Bir yöntemin veya bir özellik veya alanın türündeki geri dönüş değeri değiştirilemez. Örneğin, bir <xref:System.Object> döndürür bir yöntemin imzası bir <xref:System.String>, ya da tam tersi döndürmek için değiştirilemez.

- ❌**İzİn VERİlMEMİş: Daha önce durumu olmayan bir yapıya alan ekleme**

  Kesin atama kuralları, değişken türü durumsuz bir yapı olduğu sürece başharflenmemiş değişkenlerin kullanımına izin verir. Yapı devlet seli yapılırsa, kod başharfe çözülmemiş verilerle sonuçlanabilir. Bu hem potansiyel bir kaynak kırma ve ikili kırma değişikliğidir.

- ❌**İzİn VERİlMEMİz: Varolan bir olayı daha önce hiç ateşlemediğinde ateşlemek**

## <a name="behavioral-changes"></a>Davranış değişiklikleri

### <a name="assemblies"></a>Bütünleştirilmiş kodlar

- ✔️ **Izin VERILIR: Aynı platformlar hala desteklendiğinde montajı taşınabilir hale getirme**

- ❌**İzin VERİlMEMİş: Bir derlemenin adını değiştirme**
- ❌**İzİn VERİlMESİn: Bir derlemenin ortak anahtarını değiştirme**

### <a name="properties-fields-parameters-and-return-values"></a>Özellikler, alanlar, parametreler ve iade değerleri

- **✔️ Izin verilir: Bir özelliğin, alanın, geri dönüş değerinin veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme**

  Örneğin, bir tür döndüren <xref:System.Object> bir <xref:System.String> yöntem bir örneği döndürebilir. (Ancak, yöntem imzası değiştirilemez.)

- ✔️ **Izin: Üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse, bir özellik veya parametre için kabul edilen değerlerin aralığının artırılması**

  Yönteme geçirilebilen veya üye tarafından döndürülebilen değerler aralığı genişletilebilirken, parametre veya üye türü genişletilemez. Örneğin, bir yönteme geçirilen değerler 0-124'ten 0-255'e kadar genişletilebilirken, parametre türü ' den <xref:System.Byte> ' e <xref:System.Int32>değiştirilemez.

- ❌**İzin VERİlMEMİş: Üye sanalsa, bir özellik veya [virtual](../../csharp/language-reference/keywords/virtual.md) parametre için kabul edilen değerlerin aralığının artırılması**

   Bu değişiklik, genişletilmiş değerler aralığı için doğru çalışmayacak varolan geçersiz kılınmış üyeleri kırar.

- ❌**İzin VERİlMEMİz: Bir özellik veya parametre için kabul edilen değerlerin aralığını azaltma**

- ❌**İzin VERİlMEMİş: Bir özellik, alan, geri dönüş değeri veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma**

- ❌**İzin VERİlMEMİş: Bir özellik, alan, yöntem dönüş değeri veya [çıkış](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerleri değiştirme**

- ❌**İzin VERİlMEMİş: Bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme**

- ❌**İzin VERİlMEMİş: Sayısal bir iade değerinin kesinliği değiştirme**

- ❓ **YARGILAMA GEREKİr: Girdinin ayrıştırılmasında ve yeni istisnalar atılmasında bir değişiklik (belgelerde ayrıştırma davranışı belirtilmese bile**

### <a name="exceptions"></a>Özel durumlar

- **✔️ Izin verilir: Varolan bir özel durum daha türemiş bir özel durum atma**

  Yeni özel durum varolan bir özel durum bir alt sınıf olduğundan, önceki özel durum işleme kodu özel durum işlemeye devam eder. Örneğin, .NET Framework 4'te kültür oluşturma ve alma yöntemleri, eğer <xref:System.ArgumentException> kültürü bulunamazsa yerine bir <xref:System.Globalization.CultureNotFoundException> atamaya başladı. Çünkü <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException>türetilmiştir, bu kabul edilebilir bir değişikliktir.

- ✔️ **Izin: Daha özel <xref:System.NotSupportedException>bir <xref:System.NotImplementedException> <xref:System.NullReferenceException> istisna atma , ,**

- **✔️ Izin VERİlMeDİ: Kurtarılamaz olarak kabul edilen bir özel durum atma**

  Kurtarılamayan özel durumlar yakalanmamalı, bunun yerine üst düzey catch-all işleyicisi tarafından işlenmelidir. Bu nedenle, kullanıcıların bu açık özel durumları yakalayan bir kod olması beklenmez. Kurtarılamayan özel durumlar şunlardır:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ Izin ver: Yeni bir kod yolunda yeni bir özel durum atma**

  Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen varolan kod tarafından yürütülmeyen yeni bir kod yoluna uygulanmalıdır.

- ✔️ **Izin: Daha sağlam davranışlar veya yeni senaryolar etkinleştirmek için bir özel durum kaldırma**

  Örneğin, daha `Divide` önce yalnızca pozitif değerleri işleyen <xref:System.ArgumentOutOfRangeException> ve başka bir değer atan bir yöntem, özel durum atmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.

- ✔️ **İzİn VERİlMESİnE İzİn VERİlMESİnE: Hata iletisinin metnini değiştirme**

  Geliştiriciler, kullanıcının kültürüne bağlı olarak değişen hata iletilerinin metnine güvenmemelidir.

- ❌**İzİn VERİlMEMİz: Yukarıda listelenmemiş başka bir durumda özel durum atma**

- ❌**İzİn VERİlMEMİz: Yukarıda listelenmemiş başka bir durumda bir özel durum kaldırma**

### <a name="attributes"></a>Öznitelikler

- ✔️ **İzİn VERİlMEMİşTİr: Gözlemlenebilir *olmayan* bir özniteliğin değerini değiştirme**

- ❌**İzin VERİlMEMİş: Gözlemlenebilir *is* bir özniteliğin değerini değiştirme**

- ❓ **YARGI GEREKTIRIR: Bir özniteliği kaldırma**

  Çoğu durumda, bir öznitelik kaldırma <xref:System.NonSerializedAttribute>(gibi) bir kesme değişikliğidir.

## <a name="platform-support"></a>Platform desteği

- ✔️ **Izin verildi: Daha önce desteklenmeyen bir platformdaki bir operasyonu desteklemek**

- ❌**İzin VERİlMEMİş: Daha önce platformda desteklenen bir işlem için belirli bir hizmet paketini desteklememek veya şimdi gerektirmemek**

## <a name="internal-implementation-changes"></a>Dahili uygulama değişiklikleri

- ❓ **YARGI GEREKTIRIR: Bir iç tip yüzey alanı değiştirme**

   Özel yansımayı kırsalar da, bu tür değişikliklere genellikle izin verilir. Popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin dahili API'ler'e bağlı olduğu bazı durumlarda, bu tür değişikliklere izin verilmeyebilir.

- ❓ **KARAR GEREKTIRIR: Bir üyenin iç uygulama değiştirme**

  Özel yansımayı kırsalar da, bu değişikliklere genellikle izin verilir. Müşteri kodunun sıklıkla özel yansımaya bağlı olduğu veya değişikliğin istenmeyen yan etkilere neden olduğu bazı durumlarda, bu değişikliklere izin verilmeyebilir.

- ✔️ **Izin: Bir operasyonun performansını artırmak**

   Bir işlemin performansını değiştirme yeteneği önemlidir, ancak bu tür değişiklikler bir işlemin geçerli hızına dayanan kodu kırabilir. Bu, özellikle eşzamanlı işlemlerin zamanlamasına bağlı olarak kod için geçerlidir. Performans değişikliğinin söz konusu API'nin diğer davranışları üzerinde hiçbir etkisi olmamalıdır; aksi takdirde, değişiklik kırılıyor olacak.

- **✔️ Izin: Dolaylı olarak (ve genellikle olumsuz) bir operasyonun performansını değiştirme**

  Söz konusu değişiklik başka bir nedenle kırılma olarak kategorize edilmezse, bu kabul edilebilir. Genellikle, ek işlemler içerebilir veya yeni işlevsellik eklemek eylemleri alınması gerekir. Bu hemen hemen her zaman performansı etkileyecektir, ancak beklendiği gibi söz konusu API işlevi yapmak için gerekli olabilir.

- ❌**İzin VERİlMEZ: Senkron API'yi eşzamanlı olarak değiştirme (veya tam tersi)**

## <a name="code-changes"></a>Kod değişiklikleri

- **✔️ İzİn VERİlMESİ: Parametreye [param](../../csharp/language-reference/keywords/params.md) ekleme**

- ❌**İzin VERİlMEMİş: Bir [yapıyı](../../csharp/language-reference/builtin-types/struct.md) [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ve bunun tersi**

- ❌**İZIN VERİlMİş: [Denetlenen](../../csharp/language-reference/keywords/virtual.md) anahtar kelimeyi kod bloğuna ekleme**

   Bu değişiklik, daha önce yürütülen <xref:System.OverflowException> kodun bir atamasına neden olabilir ve kabul edilemez.

- ❌**İzİn VERİlMESİ: [Parametreden paramların](../../csharp/language-reference/keywords/params.md) çıkarılması**

- ❌**İzİn VERİlMESİ: Olayların ateşlendiği sırayı değiştirme**

  Geliştiriciler makul bir şekilde olayların aynı sırada ateş etmesini bekleyebilir ve geliştirici kodu sık sık olayların ateşlendiği sıraya bağlıdır.

- ❌**İzİn VERİlMEMİz: Belirli bir eylemde bir olayın yükseltilmesinin kaldırılması**

- ❌**İzin VERİlMEMİş: Verilen olayların kaç kez değiştirileceğinin değiştirilmesi**

- ❌**İzİn VERİlMESİn: Numaralandırma <xref:System.FlagsAttribute> türüne** ekleme
