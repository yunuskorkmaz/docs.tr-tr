---
title: Son değişiklik türleri
description: .NET Core 'un .NET sürümlerindeki geliştiriciler için uyumluluk denemelerini ve ne tür bir değişikliğin Son değişiklik olduğunu öğrenin.
ms.date: 06/10/2019
ms.openlocfilehash: bc93316141ae99d8cfedc5e6d88a9e91216f9c6e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415751"
---
# <a name="changes-that-affect-compatibility"></a>Uyumluluğu etkileyen değişiklikler

.NET, geçmişi boyunca sürümden sürüme ve .NET 'in özellikleri arasında yüksek düzeyde uyumluluk tutmaya çalıştı. Bu, .NET Core için doğru olmaya devam eder. .NET Core, .NET Framework bağımsız olan yeni bir teknoloji olarak düşünülebilir, ancak iki ana etken .NET Core 'un .NET Framework arasında sınırsız olmasına izin verebilir:

- Asıl olarak çok sayıda geliştirici geliştirmiş veya .NET Framework uygulamaları geliştirmeye devam eder. .NET uygulamalarında tutarlı davranış beklentilerine sahip olurlar.

- .NET Standard kitaplık projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API 'Leri hedefleyen kitaplıklar oluşturmalarına olanak tanır. Geliştiriciler .NET Core uygulamasında kullanılan bir kitaplığın, .NET Framework uygulamasında kullanılan aynı kitaplıkla aynı şekilde davranmasını bekler.

Geliştiriciler .NET uygulamaları genelinde uyumlulukla birlikte .NET Core sürümleri arasında yüksek düzeyde uyumluluk bekler. Özellikle .NET Core 'un önceki bir sürümü için yazılan kod, daha sonraki bir .NET Core sürümünde sorunsuz çalışmalıdır. Aslında birçok geliştirici, .NET Core 'un yeni yayımlanmış sürümlerinde bulunan yeni API 'Lerin, bu API 'Lerin tanıtıldıkları yayın öncesi sürümlerle de uyumlu olmasını bekler.

Bu makalede, uyumluluğu etkileyen değişiklikler ve .NET ekibinin her tür değişikliği değerlendirme yöntemi özetlenmektedir. .NET ekibinin olası son değişikliklere nasıl yaklaşılacağını anlamak, [mevcut .NET API](https://github.com/dotnet/runtime)'lerinin davranışını değiştiren çekme isteklerini açan geliştiriciler için özellikle yararlıdır.

Aşağıdaki bölümlerde, .NET Core API 'Lerinde yapılan değişikliklerin kategorileri ve bunların uygulama uyumluluğuyla ilgili bir etkisi açıklanır. Değişikliklere izin verilmez ✔️, izin verilmiyor ❌ veya karartan ve önceden tahmin edilebilir, belirgin ve tutarlı bir değerlendirme, önceki davranışın ❓.

> [!NOTE]
>
> - .NET kitaplıklarında yapılan değişikliklerin nasıl değerlendirildiğini gösteren bir kılavuz olarak, kitaplık geliştiricileri de bu ölçütleri kullanarak birden çok .NET uygulaması ve sürümü hedefleyen kitaplıklarında yapılan değişiklikleri değerlendirmek için de kullanılabilir.
> - Uyumluluk kategorileri hakkında daha fazla bilgi için, bkz. [Uyumluluk](categories.md), ileri ve geri uyumluluk.

## <a name="modifications-to-the-public-contract"></a>Ortak Sözleşmede yapılan değişiklikler

Bu kategorideki değişiklikler bir türün genel yüzey alanını değiştirir. Bu kategorideki değişikliklerden büyük bir olasılıkla, *geriye dönük uyumluluğu* ihlal etdiklerinden (API 'nin önceki bir sürümü ile geliştirilen bir uygulamanın daha sonraki bir sürümde yeniden derleme olmadan yürütülmesi için geliştirilmiş bir uygulama özelliği) izin verilmez.

### <a name="types"></a>Türler

- ✔️ **Izin verildi: arabirim bir temel tür tarafından zaten uygulandığında bir türden arabirim uygulamasını kaldırma**

- ❓, **Bir türe yeni bir arabirim uygulama ekleme konusunda Yargıduyuyor.**

  Bu, mevcut istemcileri olumsuz etkilemediğinden, kabul edilebilir bir değişiklik. Yeni uygulamanın kabul edilebilir olarak kalması için, bu türdeki tüm değişiklikler burada tanımlanan kabul edilebilir değişiklik sınırları içinde çalışmalıdır. Bir tasarımcının veya seri hale getiricinin alt düzey tüketilemeyecek kod veya veri oluşturma yeteneğini doğrudan etkileyen arabirimler eklenirken aşırı dikkatli olmanız gerekir. Arabirim bir örnektir <xref:System.Runtime.Serialization.ISerializable> .

- ❓, **Yeni bir temel sınıf tanıtımı gerekir**

  Bir tür, yeni bir [soyut](../../csharp/language-reference/keywords/abstract.md) üye sunmaz veya var olan türlerin semantiğini ya da davranışını değiştirmek değilse, iki mevcut tür arasında bir hiyerarşiye tanıtılamaz. Örneğin, .NET Framework 2,0 ' de, <xref:System.Data.Common.DbConnection> sınıfı <xref:System.Data.SqlClient.SqlConnection> daha önce doğrudan öğesinden türetilmiş olan için yeni bir temel sınıf haline geldi <xref:System.ComponentModel.Component> .

- ✔️ **Izin verildi: bir tür bir derlemeden diğerine taşınıyor**

  *Eski* derlemenin, <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> yeni derlemeye işaret eden ile işaretlenmesi gerekir.

- ✔️ **Izin verildi: bir [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü `readonly struct` tür olarak değiştirme**

  Tür türüne değiştirme `readonly struct` `struct` yapılmasına izin verilmez.

- ✔️ **Izin verildi: *erişilebilir* (genel veya korumalı) oluşturucular olmadığında bir türe [Sealed](../../csharp/language-reference/keywords/sealed.md) veya [abstract](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğünü ekleme**

- ✔️ **Izin verildi: bir türün görünürlüğünü genişletme**

- ❌**Izin verilmiyor: bir türün ad alanını veya adını değiştirme**

- ❌**Izin verilmiyor: ortak bir türü yeniden adlandırma veya kaldırma**

   Bu, yeniden adlandırılan veya kaldırılan türü kullanan tüm kodları keser.

- ❌**Izin verilmiyor: bir numaralandırmanın temel alınan türünü değiştirme**

   Bu bir derleme zamanı ve davranışsız değişiklik ve öznitelik bağımsız değişkenlerini ayrıştırılabilir hale getirmek için ikili bir değişiklik de yapar.

- ❌**Izin verilmiyor: daha önce korumasız bir tür mühürleme**

- ❌**Izin verilmiyor: bir arabirimin temel türleri kümesine arabirim ekleme**

   Bir arabirim daha önce uygulanmayan bir arabirim uygularsa, arabirimin orijinal sürümünü uygulayan tüm türler bozulur.

- ❓, **Bir sınıfı temel sınıflar kümesinden veya uygulanan arabirimler kümesinden bir arabirimden kaldırmak istiyor.**

  Arabirim kaldırma kuralı için bir özel durum vardır: kaldırılan arabirimden türetilen bir arabirimin uygulamasını ekleyebilirsiniz. Örneğin, <xref:System.IDisposable> türü veya arabirimi ' nin uyguladığı bir şekilde, öğesini kaldırabilirsiniz <xref:System.ComponentModel.IComponent> <xref:System.IDisposable> .

- ❌**Izin verilmiyor: bir `readonly struct` türü [struct](../../csharp/language-reference/builtin-types/struct.md) türü olarak değiştirme**

  Ancak bir tür için bir türe `struct` yapılan değişikliğe `readonly struct` izin verilir.

- ❌**Izin verilmiyor: bir [Yapı](../../csharp/language-reference/builtin-types/struct.md) türünü tür olarak değiştirme `ref struct` ve tam tersi**

- ❌**Izin verilmiyor: bir türün görünürlüğünü azaltma**

   Ancak, bir türün görünürlüğünü artırmak için izin verilir.

### <a name="members"></a>Üyeler

- ✔️ **Izin verildi: [sanal](../../csharp/language-reference/keywords/sealed.md) olmayan bir üyenin görünürlüğünü genişletme**

- ✔️ **Izin verildi: bir soyut üyeyi, *erişilebilir* (genel veya korumalı) oluşturuculara sahip olmayan bir ortak türe ekleme veya tür [mühürlü](../../csharp/language-reference/keywords/sealed.md) **

  Ancak, erişilebilir (genel veya korumalı) oluşturuculara sahip bir türe soyut üye eklenmesine `sealed` izin verilmez.

- ✔️ **Izin verildi: tür erişilebilir olmayan (ortak veya korumalı) oluşturuculara veya tür [korumalı](../../csharp/language-reference/keywords/sealed.md) olduğunda [korumalı](../../csharp/language-reference/keywords/protected.md) bir üyenin görünürlüğünü kısıtlama**

- ✔️ **Izin verildi: bir üyeyi hiyerarşide daha yüksek bir sınıfa, onun kaldırıldığı türden daha yukarıya taşıma**

- ✔️ **Izin verilen: bir geçersiz kılma ekleme veya kaldırma**

  Bir geçersiz kılma ile tanışın, önceki tüketicilere [taban](../../csharp/language-reference/keywords/base.md)çağrılırken geçersiz kılma üzerinde atlama yapılmasına neden olabilir.

- ✔️ **Izin verildi: sınıfın daha önce Oluşturucusu yoksa, bir sınıfa Oluşturucu Ekleme, parametresiz bir oluşturucuyla birlikte**

   Ancak, parametresiz oluşturucuyu eklemeden daha önceden hiç oluşturucuya *sahip olmayan bir* sınıfa bir Oluşturucu eklemeye izin verilmez.

- ✔️ **Izin verildi: bir üyeyi [soyut](../../csharp/language-reference/keywords/abstract.md) Iken [sanal](../../csharp/language-reference/keywords/virtual.md) olarak değiştirme**

- ✔️ **Izin verildi: bir `ref readonly` `ref` dönüş değerine değiştirme (sanal yöntemler veya arabirimler hariç)**

- ✔️ **Izin verildi: alanın statik türü kesilebilir değer türünde değilse, bir alandan [ReadOnly](../../csharp/language-reference/keywords/readonly.md) öğesini kaldırma**

- ✔️ **Izin verildi: daha önce tanımlanmayan yeni bir olay çağrılıyor**

- ❓, **Bir türe yeni bir örnek alanı ekleme konusunda Yargıduyuyor**

   Bu değişiklik Serileştirmeyi etkiler.

- ❌**Izin verilmiyor: ortak bir üyeyi veya parametreyi yeniden adlandırma veya kaldırma**

   Bu, yeniden adlandırılan veya kaldırılan üyeyi veya parametreyi kullanan tüm kodları keser.

   Bu, bir alıcı veya ayarlayıcının bir özellikten kaldırılmasını veya yeniden adlandırılmasını, ayrıca sabit listesi üyelerini yeniden adlandırmayı veya kaldırmayı içerir.

- ❌**Izin verilmiyor: arabirime üye ekleme**

- ❌**Izin verilmiyor: bir genel sabit veya numaralandırma üyesinin değerini değiştirme**

- ❌**Izin verilmiyor: bir özelliğin, alanın, parametrenin veya dönüş değerinin türünü değiştirme**

- ❌**Izin verilmiyor: parametre sırasını ekleme, kaldırma veya değiştirme**

- ❌**Izin verilmiyor: bir parametreden [ın](../../csharp/language-reference/keywords/in.md), [Out](../../csharp/language-reference/keywords/out.md) veya [ref](../../csharp/language-reference/keywords/ref.md) anahtar sözcüğünü ekleme veya kaldırma**

- ❌**Izin verilmiyor: bir parametreyi yeniden adlandırma (büyük küçük harf değişikliği dahil)**

  Bunun iki nedenden dolayı bölünmesi kabul edilir:

  - C# ' de Visual Basic ve [Dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) ' deki geç bağlama özelliği gibi geç bağlantılı senaryoları keser.

  - Geliştiriciler [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)kullandıklarında [kaynak uyumluluğunu](categories.md#source-compatibility) keser.

- ❌**Izin verilmiyor: `ref` dönüş değerinden `ref readonly` dönüş değerine değiştirme**

- ❌️**Izin verilmiyor: bir `ref readonly` `ref` sanal yöntem veya arabirimdeki bir dönüş değerine değiştirme**

- ❌**Izin verilmiyor: bir üyeden [Özet](../../csharp/language-reference/keywords/abstract.md) ekleme veya kaldırma**

- ❌**Izin verilmiyor: [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü bir üyeden kaldırma**

  C# derleyicisi, sanal olmayan yöntemleri çağırmak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) ara DIL (IL) yönergelerini yayma eğilimi gösterirken (bir `callvirt` null denetimi gerçekleştirir, normal bir çağrı olmadığında), bu davranış çeşitli nedenlerle ınvariable değildir:
  - C#, .net 'in hedeflediği tek dil değildir.

  - C# derleyicisi, `callvirt` hedef yöntem sanal olmayan ve muhtemelen null olmadığında ( [?. null yayma operatörü](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)aracılığıyla erişilen bir yöntem gibi) normal bir çağrıyı en iyi şekilde iyileştirmenize çalışır.

  Bir yöntem sanal hale getirmek, tüketici kodunun genellikle neredeyse bir kez çağrılmasını sona erdirmek anlamına gelir.

- ❌**Izin verilmiyor: bir üyeye [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcük ekleme**

- ❌**Izin verilmiyor: bir sanal üyeyi soyut hale getirme**

  Bir [sanal üye](../../csharp/language-reference/keywords/virtual.md) , türetilmiş bir sınıf tarafından *geçersiz kılınabilen bir* Yöntem uygulamasını sağlar. [Soyut üye](../../csharp/language-reference/keywords/abstract.md) , uygulama sağlamaz ve geçersiz *kılınmalıdır* .

- ❌**Izin verilmiyor: erişilebilir (genel veya korumalı) oluşturuculara ve [korumalı](../../csharp/language-reference/keywords/sealed.md) olmayan bir ortak türe soyut üye ekleme**

- ❌**Izin verilmiyor: üyenin [statik](../../csharp/language-reference/keywords/static.md) anahtar sözcüğünü ekleme veya kaldırma**

- ❌**Izin verilmiyor: var olan bir aşırı yüklemeyi engelleyen ve farklı bir davranışı tanımlayan bir aşırı yükleme ekleniyor**

  Bu, önceki aşırı yüklemeye bağlanan mevcut istemcileri keser. Örneğin, bir sınıfın bir yöntemi kabul eden tek bir sürümü varsa <xref:System.UInt32> , var olan bir tüketici bir değer geçirirken bu aşırı yüklemeye başarıyla bağlanır <xref:System.Int32> . Ancak, kabul eden bir aşırı yükleme eklerseniz <xref:System.Int32> veya geç bağlamayı kullandığınızda, derleyici artık yeni aşırı yüklemeye bağlanır. Farklı davranış sonuç alıyorsa, bu durum bir son değişiklik olur.

- ❌**Izin verilmiyor: parametresiz oluşturucuyu eklemeden daha önce Oluşturucusu olmayan bir sınıfa Oluşturucu Ekleme**

- ❌️**Izin verilmiyor: bir alana [ReadOnly](../../csharp/language-reference/keywords/readonly.md) ekleme**

- ❌**Izin verilmiyor: üyenin görünürlüğünü azaltma**

   Bu, *erişilebilir* ( [protected](../../csharp/language-reference/keywords/protected.md) `public` veya `protected` ) oluşturucular olduğunda ve tür *not* [korumalı](../../csharp/language-reference/keywords/sealed.md)olmadığında korunan bir üyenin görünürlüğünü azaltmayı içerir. Bu durumda, korunan bir üyenin görünürlüğünü azaltmak için izin verilir.

   Üyenin görünürlüğünü artırmak için izin verilir.

- ❌**Izin verilmiyor: üyenin türünü değiştirme**

   Bir metodun veya bir özelliğin ya da alanın dönüş değeri değiştirilemez. Örneğin, döndüren bir yöntemin imzası <xref:System.Object> , bir veya döndürmek için değiştirilemez <xref:System.String> .

- ❌**Izin verilmiyor: daha önce durumu olmayan bir yapıya alan ekleme**

  Kesin atama kuralları, değişken türü durum bilgisi olmayan bir yapı olduğu sürece başlatılmamış değişkenlerin kullanılmasına izin verir. Yapı durum bilgisi olarak yapılırsa, kod başlatılmamış verilerle bitebilecek. Bu, büyük olasılıkla kaynak bölünmesi ve ikili bir değişiklik değişikliği olur.

- ❌**Izin verilmiyor: daha önce hiç tetiklendiğinde var olan bir olayı tetikleme**

## <a name="behavioral-changes"></a>Davranış değişiklikleri

### <a name="assemblies"></a>Bütünleştirilmiş Kodlar

- ✔️ **Izin verildi: aynı platformlar hala desteklenmeden bir derlemeyi taşınabilir hale getirme**

- ❌**Izin verilmiyor: bir derlemenin adını değiştirme**
- ❌**Izin verilmiyor: bir derlemenin ortak anahtarını değiştirme**

### <a name="properties-fields-parameters-and-return-values"></a>Özellikler, alanlar, parametreler ve dönüş değerleri

- **Izin verilen ✔️: bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresinin değerini daha türetilmiş bir türe değiştirme**

  Örneğin, bir türü döndüren bir yöntem <xref:System.Object> bir <xref:System.String> örnek döndürebilir. (Ancak, yöntem imzası değiştirilemez.)

- ✔️ **Izin verildi: üye [sanal](../../csharp/language-reference/keywords/virtual.md) değilse, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma**

  Yönteme geçirilebilecek veya üye tarafından döndürülen değer aralığı genişken, parametre veya üye türü ' ni genişletebilirler. Örneğin, bir yönteme geçirilen değerler 0-124 ' den 0-255 ' e genişleyebilir, parametre türü ' dan ' a geçiş yapılamaz <xref:System.Byte> <xref:System.Int32> .

- ❌**Izin verilmiyor: üye [sanal](../../csharp/language-reference/keywords/virtual.md) ise, bir özellik veya parametre için kabul edilen değerlerin aralığını artırma**

   Bu değişiklik, genişletilmiş değer aralığı için doğru şekilde çalışmayacak olan geçersiz kılınan üyeleri keser.

- ❌**Izin verilmiyor: bir özellik veya parametre için kabul edilen değerlerin aralığını azaltma**

- ❌**Izin verilmiyor: bir özellik, alan, dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi için döndürülen değerlerin aralığını artırma**

- ❌**Izin verilmiyor: bir özellik, alan, yöntem dönüş değeri veya [Out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi Için döndürülen değerleri değiştirme**

- ❌**Izin verilmiyor: bir özelliğin, alanın veya parametrenin varsayılan değerini değiştirme**

- ❌**Izin verilmiyor: sayısal bir dönüş değerinin hassasiyetini değiştirme**

- ❓ **, Giriş ayrıştırması ve yeni özel durumlar oluşturmadaki bir değişiklik olmalıdır (ayrıştırma davranışı belgelerde belirtilmese bile).**

### <a name="exceptions"></a>Özel durumlar

- ✔️ **Izin verilen: var olan bir özel durumdan daha fazla türetilmiş özel durum üretiliyor**

  Yeni özel durum var olan bir özel durumun alt sınıfı olduğundan, önceki özel durum işleme kodu özel durumu işlemeye devam eder. Örneğin, .NET Framework 4 ' te kültür oluşturma ve alma yöntemleri kültür bulunamazsa bir yerine bir oluşturmaya başlamıştır <xref:System.Globalization.CultureNotFoundException> <xref:System.ArgumentException> . <xref:System.Globalization.CultureNotFoundException>Öğesinden türetildiğinden <xref:System.ArgumentException> , bu kabul edilebilir bir değişiklik.

- ✔️ **Izin verildi: <xref:System.NotSupportedException> <xref:System.NotImplementedException> <xref:System.NullReferenceException> şundan daha özel bir özel durum üretiliyor** ,

- ✔️ **Izin verildi: kurtarılamaz olarak kabul edilen bir özel durum üretiliyor**

  Kurtarılamaz özel durumlar yakalanmamalıdır, bunun yerine üst düzey bir catch-all işleyicisi tarafından işlenmelidir. Bu nedenle, kullanıcıların bu açık özel durumları yakalayan kodun olması beklenmez. Kurtarılamaz özel durumlar şunlardır:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **Izin verilen: yeni bir kod yolunda yeni bir özel durum üretiliyor**

  Özel durum yalnızca yeni parametre değerleri veya durumuyla yürütülen ve önceki sürümü hedefleyen mevcut kodla yürütülemeyen yeni bir kod yolu için geçerli olmalıdır.

- ✔️ **Izin verildi: daha sağlam davranışı veya yeni senaryoları etkinleştirmek için özel durumu kaldırma**

  Örneğin, `Divide` daha önce yalnızca pozitif değerleri işlenmiş ve başka bir şekilde oluşturulmuş bir yöntem, <xref:System.ArgumentOutOfRangeException> özel durum oluşturmadan hem negatif hem de pozitif değerleri destekleyecek şekilde değiştirilebilir.

- ✔️ **Izin verilen: hata iletisi metnini değiştirme**

  Geliştiriciler, kullanıcının kültürüne göre de değişen hata iletilerinin metnine güvenmemelidir.

- ❌**Izin verilmiyor: Yukarıda listelenmeyen başka bir durumda özel durum üretiliyor**

- ❌**Izin verilmiyor: Yukarıda listelenmeyen herhangi bir özel durumu kaldırma**

### <a name="attributes"></a>Öznitelikler

- ✔️ **Izin verildi: observable *olmayan* bir özniteliğin değerini değiştirme**

- ❌**Izin verilmiyor: observable olan bir özniteliğin değerini değiştirme *is* **

- ❓, **Bir özniteliği kaldırmak IÇIN Yargıduyuyor**

  Çoğu durumda, bir özniteliği (gibi) kaldırmak, önemli <xref:System.NonSerializedAttribute> bir değişiklik olur.

## <a name="platform-support"></a>Platform desteği

- ✔️ **Izin verildi: daha önce desteklenmeyen bir platformda Işlem destekleme**

- ❌**Izin verilmeyen: bir platformda daha önce desteklenen bir işlem için belirli bir hizmet paketini desteklemiyor veya artık gerektirmiyor**

## <a name="internal-implementation-changes"></a>İç uygulama değişiklikleri

- ❓ **, Bir iç türün yüzey alanını değiştirmek Için gereken bır yargıdır.**

   Bu tür değişikliklere genel olarak izin verilir, ancak özel yansımayı keser. Bazı durumlarda, popüler üçüncü taraf kitaplıklarının veya çok sayıda geliştiricinin iç API 'Lere bağlı olduğu durumlarda, bu değişikliklere izin verilmiyor olabilir.

- ❓ **, Bir üyenin iç uygulamasını değiştirme konusunda Yargıduyuyor**

  Bu değişikliklere genel olarak izin verilir, ancak özel yansımayı keser. Bazı durumlarda, müşteri kodunun genellikle özel yansımaya bağlı olması veya değişikliğin istenmeyen yan etkileri sağlaması durumunda bu değişikliklere izin verilmiyor olabilir.

- ✔️ **Izin verildi: bir işlemin performansını artırma**

   Bir işlemin performansını değiştirme yeteneği zorunludur, ancak bu tür değişiklikler bir işlemin geçerli hızına bağlı kodu kesebilir. Bu, özellikle de zaman uyumsuz işlemlerin zamanlamasına bağlı olan kodun bir doğrudur. Performans değişikliğinin, söz konusu API 'nin diğer davranışları üzerinde hiçbir etkisi olmamalıdır; Aksi takdirde, değişiklik koparacaktır.

- ✔️ **Izin verildi: dolaylı (ve çoğunlukla olumsuz) bir işlemin performansını değiştirme**

  Söz konusu değişiklik başka bir nedenden dolayı bölme olarak kategorilere ayrılmazsa, bu kabul edilebilir. Genellikle, ek işlemleri içerebilen veya yeni işlevsellik ekleyen eylemlerin alınması gerekir. Bu, neredeyse her zaman performansı etkiler ancak API 'yi soru işlevinin beklendiği gibi yapmak için gerekli olabilir.

- ❌**Izin verilmiyor: zaman uyumlu bır API 'yi zaman uyumsuz (ve tam tersi) olarak değiştirme**

## <a name="code-changes"></a>Kod değişiklikleri

- ✔️ **Izin verilen: parametreye [params](../../csharp/language-reference/keywords/params.md) ekleme**

- ❌**Izin verilmiyor: bir [yapıyı](../../csharp/language-reference/builtin-types/struct.md) bir [sınıfa](../../csharp/language-reference/keywords/class.md) değiştirme ve tam tersi**

- ❌**Izin verilmiyor: [Checked](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğünü bir kod bloğuna ekleme**

   Bu değişiklik, daha önce bir ve oluşturması için yürütülen kodun <xref:System.OverflowException> kabul edilemez olmasını sağlayabilir.

- ❌**Izin verilmiyor: parametrelerin [parametreleri](../../csharp/language-reference/keywords/params.md) kaldırılıyor**

- ❌**Izin verilmiyor: olayların tetiklenme sırasını değiştirme**

  Geliştiriciler, olayların aynı sırayla tetiklenmesi makul bir şekilde bekleyebilir ve geliştirici kodu genellikle olayların tetikleneceği sıraya bağlıdır.

- ❌**Izin verilmiyor: belirli bir eylemde olay oluşturma Işlemi kaldırılıyor**

- ❌**Izin verilmiyor: verilen olayların sayısını değiştirme**

- ❌**Izin verilmiyor: <xref:System.FlagsAttribute> bir numaralandırma türüne ekleme**
