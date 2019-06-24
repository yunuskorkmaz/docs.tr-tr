---
title: .NET Core bozucu değişiklikleri - değerlendir
description: .NET Core, geliştiriciler için .NET sürümleri arasında uyumluluk sağlamak çalışır yolları hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: b58edd9ff0bd56b12b861162cc92d484a3b36c8b
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307501"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>.NET core'da bozucu değişiklikleri değerlendir

Buna ait geçmişi, sürüme ve .NET türü arasında uyumluluk sürümden yüksek bir düzeyde korumak .NET çalıştı. Bu, .NET Core için doğru devam eder. .NET Core .NET Framework bağımsız olan yeni bir teknoloji kabul edilebilir olsa da, .NET Core yeteneğini .NET Framework'ten ayırmak için iki ana Etkenler sınırla:

- Geliştiricilerin çok sayıda ilk olarak geliştirilen veya .NET Framework uygulamaları geliştirmeye devam. .NET uygulamaları arasında tutarlı bir davranış beklerler.

- .NET standard kitaplığı projeleri, geliştiricilerin .NET Core ve .NET Framework tarafından paylaşılan ortak API'ler hedefleyen kitaplıklar sağlar. Geliştiriciler için kullanılan bir .NET Framework uygulamasında aynı kitaplığı bir .NET Core uygulamasında kullanılan bir kitaplık aynı şekilde davranır bekler.

.NET uygulamaları üzerinde daha fazla uyumluluk yanı sıra, geliştiricilerin .NET Core sürümleri arasında uyumluluk yüksek düzeyde bekler. Özellikle, .NET Core önceki bir sürümü için yazılan kod sorunsuz bir şekilde .NET Core daha sonraki bir sürümünü çalıştırmalısınız. Aslında, geliştiricilerin çoğu, yeni yayımlanmış bir .NET Core sürümlerinde bulunan yeni API'ler Ayrıca, bu API'leri kullanıma sunulan yayın öncesi sürümleriyle uyumlu olacağını bekler.

Bu makalede, kategorileri uyumluluk değişiklikleri (veya önemli değişiklikler) ve değişiklikleri Bu kategorilerden her biri, .NET ekibi değerlendirir bir şekilde açıklanmaktadır. .NET ekibi olası yeni değişikliklerin nasıl yaklaşıyor anlamak, çekme isteklerinde açmakta olduğunuz geliştiriciler için özellikle yararlı [dotnet/corefx'te](https://github.com/dotnet/corefx) mevcut API'lere davranışını değiştirmek GitHub deposu.

> [!NOTE]
> İkili uyumluluğu ve geriye dönük uyumluluk gibi uyumluluk kategori tanımı için bkz. [bozucu değişiklik kategorileri](categories.md).

Aşağıdaki bölümlerde, .NET Core API'ları ve bunların uygulama uyumluluğunu etkileyen değişiklikler kategorileri açıklanmaktadır. Belirli bir değişiklik türünü izin verilen, izin verilmez ve ❓ olabilir veya izin verilmemiş bir değişikliği belirtir ❌ gösterir ✔️ simgesi gösterir. Bu son kategori değişiklikler kararı gerektirir ve önceki davranışı nasıl öngörülebilir, açık ve tutarlı bir değerlendirme idi.

> [!NOTE]
> .NET Core kitaplıklarda yapılan değişiklikler nasıl değerlendirilir yönelik bir kılavuz olarak hizmet veren yanı sıra kitaplığı geliştiriciler de bu ölçütleri birden çok .NET uygulamaları ve sürümlerini hedefleyen, kitaplıklarda yapılan değişiklikler değerlendirmek için kullanabilirsiniz.

## <a name="modifications-to-the-public-contract"></a>Genel sözleşme değişiklikler

Bu kategorideki değişiklikleri *değiştirme* genel yüzey alanı türü. Bunlar ihlal olduğundan bu kategorideki değişikliklerin çoğu izin verilmeyen *geriye dönük uyumluluk* (gerekmeksizin sonraki sürüm üzerinde yürütme yeteneği geliştirilen bir uygulamanın bir API önceki bir sürümü ile).

### <a name="types"></a>Türler

- **Arabirim zaten bir taban türü tarafından uygulandığında, bir arabirim uygulaması bir türden kaldırmayı ✔️**

- **❓ türüne yeni bir arabirim uygulaması ekleme**

  Mevcut istemcilerin olumsuz etkilemez çünkü bu kabul edilebilir bir değişikliktir. Herhangi bir değişiklik türü kabul edilebilir değişiklikler kabul edilebilir kalması için yeni uygulama burada tanımlanan sınırları içinde çalışmanız gerekir. Bir tasarımcı yeteneğini doğrudan etkileyen arabirimleri eklerken son derece dikkatli olun gereklidir veya alt düzey seri hale getirici kod veya olamaz veri oluşturmak için kullanılan. Bir örnek <xref:System.Runtime.Serialization.ISerializable> arabirimi.

- **❓ Yeni bir temel sınıf ile tanışın**

  Var olan iki tür arasında bir hiyerarşiye herhangi yeni tanıtmak değil, bir tür tanıtılabilir [soyut](../../csharp/language-reference/keywords/abstract.md) üyeleri veya semantiği ya da varolan türleri davranışını değiştirin. Örneğin, .NET Framework 2.0 içinde <xref:System.Data.Common.DbConnection> sınıfı için yeni bir temel sınıf dönüştü <xref:System.Data.SqlClient.SqlConnection>, hangi önceden türetilen doğrudan <xref:System.ComponentModel.Component>.

- **✔️ bir derlemeden bir tür taşıma**

  Unutmayın *eski* derleme ile işaretlenmeli <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> işaret eden yeni bir derleme.

- **✔️ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için yazın bir `readonly struct` türü**

  Not Bu değiştirme bir `readonly struct` için yazın bir `struct` türüne izin verilmiyor.
  
- **✔️ Ekleme [korumalı](../../csharp/language-reference/keywords/sealed.md) veya [soyut](../../csharp/language-reference/keywords/abstract.md) anahtar sözcüğü bir tür olduğunda için hiçbir *erişilebilir* oluşturucular (ortak veya korumalı)**

- **Bir tür görünürlüğünü genişletme ✔️**

- **❌ ad alanı veya bir türün adını değiştirme**

- **❌ yeniden adlandırma veya bir genel tür kaldırılıyor**

   Bu, yeniden adlandırılmış veya kaldırılmış türünü kullanan tüm kodları keser.

- **Temel alınan bir numaralandırma türünün değiştirilmesi ❌**

   Öznitelik bağımsız değişkenleri ayrıştırılamayan yapabilen bir ikili değişiklik yanı sıra derleme zamanı ve değişiklik davranış budur.

- **Daha önce korumasız bir tür mühürleme ❌**

- **❌ Arabirim bir arabirimin temel türleri kümesine ekleme**

   Bir arabirim, daha önce uygulamaz bir arabirim uygularsa, özgün sürümle arabirimin uygulanan tüm türleri kesilir.

- **Bir sınıfın temel sınıf veya arabirimin uygulanan arabirimleri kümesinden kümesinden kaldırma ❓**

  Arabirimi kaldırma kuralı için bir istisna vardır: kaldırılan arabirimden türetilmiş bir arabirim uygulaması ekleyebilirsiniz. Örneğin, kaldırabilirsiniz <xref:System.IDisposable> türü veya arabirim artık uyguluyorsa <xref:System.ComponentModel.IComponent>, uygulayan <xref:System.IDisposable>.

- **❌ Değiştirme bir `readonly struct` için yazın bir [yapı](../../csharp/language-reference/keywords/struct.md) türü**

  Unutmayın, değişikliği bir `struct` için yazın bir `readonly struct` türüne izin verilir.

- **❌ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için yazın bir `ref struct` türü ve bunun tersi de geçerlidir**

- **Bir tür görünürlüğünü azaltma ❌**

   Ancak, bir tür görünürlüğünü artırmak izin verilir.

### <a name="members"></a>Üyeler

- **Olmayan bir üye görünürlüğünü genişletme ✔️ [sanal](../../csharp/language-reference/keywords/sealed.md)**

- **Bir soyut üye olmayan genel bir tür ekleme ✔️ *erişilebilir* (ortak veya korumalı) oluşturucular veya türündeki [korumalı](../../csharp/language-reference/keywords/sealed.md)**

  Ancak, bir soyut üye (ortak veya korumalı) erişilebilir oluşturucuya sahip değil ve olmayan bir türe ekleme `sealed` izin verilmiyor.

- **Görünürlüğü kısıtlamak ✔️ bir [korumalı](../../csharp/language-reference/keywords/protected.md) türü (ortak veya korumalı) hiçbir erişilebilir oluşturucuya sahip veya bu tür, üye [korumalı](../../csharp/language-reference/keywords/sealed.md)**

- **Bir sınıf içinden kaldırıldı türünden hiyerarşinin üst düzeylerindeki üyesi taşınmasını ✔️**

- **✔️ Ekleme veya kaldırma bir geçersiz kılma**

  Bir geçersiz kılma ile tanışın çağırırken geçersiz kılma atlamak önceki tüketiciler yol açabileceğini unutmayın [temel](../../csharp/language-reference/keywords/base.md).

- **✔️ sınıfı daha önce hiç Oluşturucusu varsa varsayılan (parametresiz) bir Oluşturucu ile birlikte bir sınıf oluşturucu ekleme**

   Ancak, daha önce hiç Oluşturucusu olan bir sınıf için bir oluşturucu eklemesini *olmadan* varsayılan oluşturucu eklemesini izin verilmiyor.

- **Bir üye değiştirme ✔️ [soyut](../../csharp/language-reference/keywords/abstract.md) için [sanal](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ gelen değiştirerek bir `ref readonly` için bir `ref` dönüş değeri (hariç, sanal yöntemleri veya arabirimi)**

- **✔️ Kaldırma [salt okunur](../../csharp/language-reference/keywords/readonly.md) statik türü sürece bir alandan alan bir değişmez değer türü olduğu.**

- **Daha önce tanımlanmadı yeni bir olayı çağırmak ✔️**

- **❓ türüne yeni bir örneğini alan ekleme**

   Bu değişiklik, serileştirme etkiler.

- **❌ yeniden adlandırma veya bir ortak üye veya parametre kaldırılıyor**

   Bu yeniden adlandırılmış veya kaldırılmış üyesi veya parametre kullanan tüm kodları keser.

   Bir alıcı veya ayarlayıcı yeniden adlandırma ya da kaldırma numaralandırma üyelerini yanı sıra bir özellik, yeniden adlandırma ya da kaldırma içerdiğini unutmayın.

- **❌ bir arabirim üye ekleme**

- **Genel bir sabit veya sabit listesi üyesi değerinin değiştirilmesi ❌**

- **❌ bir özellik, alan, parametre veya dönüş değeri türünü değiştirme**

- **❌ Ekleme, kaldırma veya parametrelerinin sırasını değiştirme**

- **❌ Ekleme veya kaldırma [içinde](../../csharp/language-reference/keywords/in.md), [kullanıma](../../csharp/language-reference/keywords/out.md) , veya [ref](../../csharp/language-reference/keywords/ref.md) parametre from anahtar sözcüğü**

- **❌ (kasasının değiştirme dahil) bir parametre yeniden adlandırma**

  Bu, iki nedenden dolayı bozucu olarak kabul edilir:
  
  - Visual Basic'te geç bağlama senaryoları geç bağlama özelliği gibi ayırır ve [dinamik](../../csharp/language-reference/keywords/dynamic.md) içinde C#.
  
  - Bunu keser [kaynağı Uyumluluk](categories.md#source-compatibility) geliştiriciler kullandığınızda [adlandırılmış bağımsız değişkenler](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- **❌ gelen değiştirerek bir `ref` dönüş değeri için bir `ref readonly` dönüş değeri**

- **❌️ gelen değiştirerek bir `ref readonly` için bir `ref` dönüş değeri bir sanal yöntem veya arabirimi**

- **❌ Ekleme veya kaldırma [soyut](../../csharp/language-reference/keywords/abstract.md) bir üyesinin**

- **❌ Kaldırma [sanal](../../csharp/language-reference/keywords/virtual.md) üyesi from anahtar sözcüğü**

  Bu genellikle bir değişiklik olmadığından sırada C# derleyici eğilimlidir yaymak için [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) sanal olmayan yöntemleri çağırmak için Ara dil (IL) yönergeleri (`callvirt` olmayan normal bir çağrı sırasında bir null kontrolü gerçekleştirir ), bu davranışı çeşitli nedenlerle invariable değil:
  - C#değil yalnızca .NET hedefleyen dilidir.
  
  - C# Derleyici giderek çalıştığında en iyi duruma getirme `callvirt` hedef yöntemi sanal olmayan ve null büyük olasılıkla her bir normal arama (aracılığıyla erişilen bir yöntemi gibi [?. null yayılma işleci](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).
  
  Sanal bir yöntem yapma, sanal olmayan arama, tüketici kod genellikle umduğunuz anlamına gelir.

- **❌ Ekleme [sanal](../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü bir üye**

- **Bir sanal üye soyut yapmak ❌**

  A [sanal üye](../../csharp/language-reference/keywords/virtual.md) sağlayan bir yöntem uygulaması *olabilir* türetilmiş sınıf tarafından geçersiz kılındı. Bir [soyut üye](../../csharp/language-reference/keywords/abstract.md) uygulaması sağlar ve *olmalıdır* geçersiz kılındı.

- **Bir soyut üye ekleme ve erişilebilir (ortak veya korumalı) bir oluşturucuya sahip ortak bir türe ❌ değil [korumalı](../../csharp/language-reference/keywords/sealed.md)**

- **❌ Ekleme veya kaldırma [statik](../../csharp/language-reference/keywords/static.md) üyesi from anahtar sözcüğü**

- **Var olan bir aşırı ışığının ve farklı bir davranış tanımlayan bir aşırı yüklemesini eklemeyi ❌**

  Bu, önceki aşırı yüklemesine bağlı olan mevcut istemcilerin keser. Örneğin, bir sınıf yönteminin tek bir sürüm varsa kabul eden bir <xref:System.UInt32>, geçerken var olan bir tüketici başarıyla için aşırı yükleyen bağlayacaksınız bir <xref:System.Int32> değeri. Ancak, bir aşırı eklerseniz kabul eden bir <xref:System.Int32>, yeniden derlemeden ya da geç bağlama kullanarak, derleyici artık yeni aşırı bağlar. Farklı bir davranış sonuçlanırsa, bir değişiklik budur.

- **❌ önceden varsayılan oluşturucu eklemeden hiçbir oluşturucu sahip olan bir sınıf oluşturucu ekleme**

- **❌️ Ekleme [salt okunur](../../csharp/language-reference/keywords/readonly.md) bir alana**

- **Üye görünürlüğü azaltma ❌**

   Bu görünürlüğünü azaltmayı içerir bir [korumalı](../../csharp/language-reference/keywords/protected.md) olduğunda üye *erişilebilir* (ortak veya korumalı) oluşturucular ve türü *değil* [ korumalı](../../csharp/language-reference/keywords/sealed.md). Durum bu değilse, korumalı bir üye görünürlüğünü azaltma izin verilir.

   Üye görünürlüğünü artırmak izin verildiğini unutmayın.

- **❌ üye türünü değiştirme**

   Bir yöntem veya özellik veya alan türünü dönüş değeri değiştirilemez. Örneğin, döndüren bir yöntem imzası bir <xref:System.Object> döndürülecek değiştirilemez bir <xref:System.String>, ya da tam tersi.

- **❌ durumu olmadan önceden var olan bir yapı için bir alan ekleme**

  Durum bilgisi olmayan bir yapı değişken türü olduğu sürece belirli atama onayına kuralları başlatılmamış değişkenler kullanımına izin verin. Struct durum bilgisi olan yaptıysanız, kod ile başlatılmamış veri bulunabileceğini. Potansiyel olarak yeni bir kaynak hem de yeni değişiklik bir ikili budur.

- **❌ hiçbir zaman önce harekete geçirildi var olan bir olay tetikleme**

## <a name="behavioral-changes"></a>Davranış değişiklikleri

### <a name="assemblies"></a>Bütünleştirilmiş kodlar

- **✔️ aynı platformlarda hala desteklendiğinde derleme taşınabilir hale getirme**

- **Bir derleme adının değiştirilmesi ❌**
- **Bir derlemenin ortak anahtarı değiştirme ❌**

### <a name="properties-fields-parameters-and-return-values"></a>Özellikler, alanlar, parametreler ve dönüş değerleri

- **Bir özellik, alan, dönüş değeri değerinin değiştirilmesi ✔️ veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) daha türetilmiş bir tür parametresi**

  Örneğin, bir tür döndüren bir yöntem <xref:System.Object> döndürebilir bir <xref:System.String> örneği. (Ancak, yöntem imzası değiştiremezsiniz.)

- **Aralığını artırma ✔️ üyesi değilse, özelliği veya parametre değerlerini kabul [sanal](../../csharp/language-reference/keywords/virtual.md)**

  Not yönteme geçirilen veya üye tarafından döndürülen değer aralığını genişletebilirsiniz olsa da parametre veya üye türü olamaz. Bir yönteme değerleri 0-124 0-255'e genişletebilirsiniz kullanılırken, örneğin, parametre türü alanından değiştirilemez <xref:System.Byte> için <xref:System.Int32>.

- **Aralığını artırma ❌ üyesiyse bir özellik veya parametre değerlerini kabul [sanal](../../csharp/language-reference/keywords/virtual.md)**

   Bu değişiklik, genişletilmiş değer aralığı için düzgün şekilde çalışmaz mevcut geçersiz kılınan üye keser.

- **Bir özellik veya parametresi için kabul edilen değerler aralığının azaltılması ❌**

- **Aralığını artırma ❌ döndürülen değerlerin bir özellik, alan, dönüş değeri veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi**

- **❌ döndürülen bir özellik, alan, yöntem dönüş değeri, değiştirerek veya [kullanıma](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi**

- **Bir özellik, alan veya parametre varsayılan değerinin değiştirilmesi ❌**

- **❌ sayısal dönüş değeri duyarlığını değiştirme**

- **Giriş ayrıştırma ve (ayrıştırma davranışının belgelerinde belirtilmemiş olsa bile, yeni özel durumları atma ❓ bir değişim**

### <a name="exceptions"></a>Özel Durumlar

- **Var olan bir özel durum daha fazla türetilmiş bir özel durum ✔️**

  Yeni özel durum var olan bir özel durum öğesinin olduğundan, önceki özel durum işleme kodunu özel durumu işlemek üzere devam eder. Örneğin, .NET Framework 4'te kültürü oluşturma ve alma yöntemleri throw başladığı bir <xref:System.Globalization.CultureNotFoundException> yerine bir <xref:System.ArgumentException> , kültür bulunamadı. Çünkü <xref:System.Globalization.CultureNotFoundException> türetildiği <xref:System.ArgumentException>, bu kabul edilebilir bir değişikliktir.

- **Daha fazla belirli bir özel durum ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**

- **✔️ kurtarılamaz olarak kabul edilen bir özel durum**

  Kurtarılamaz bir özel durum yakalanmadı, ancak bunun yerine üst düzey bir genel işleyici tarafından yapılması gerekir. Bu nedenle, kullanıcıların açık bu özel durumlarını yakalayan kodu olması beklenmez. Kurtarılamaz bir özel durumlar şunlardır:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **Yeni bir kod yolunda yeni bir özel durum atma ✔️**

  Özel durum yalnızca yeni bir kod-yeni parametre değerlerini veya durumu ile yürütülür ve varolan kodu tarafından yürütülemez yol hedefleyen önceki sürümü uygulamanız gerekir.

- **✔️ daha sağlam bir davranış veya yeni senaryoları etkinleştirmek için bir özel durum kaldırılıyor**

  Örneğin, bir `Divide` daha önce yalnızca pozitif değerlere işlenmiş ve oluşturdu yöntemi bir <xref:System.ArgumentOutOfRangeException> yoksa bir özel durum oluşturmadan hem negatif hem pozitif değerleri destekleyecek şekilde değiştirilebilir.

- **✔️ bir hata iletisinin metni değiştirme**

  Geliştiriciler, kullanıcının kültüre göre de değişir hata iletileri metin dayanarak doğrulamamalısınız.

- **Yukarıda örnekte bir özel durum ❌**

- **❌ Yukarıda listelenmeyen diğer durumda bir özel durum kaldırılıyor**

### <a name="attributes"></a>Öznitelikler

- **Bir öznitelik değerinin değiştirilmesi ✔️ *değil* observable**

- **Bir öznitelik değerinin değiştirilmesi ❌, *olduğu* observable**

- **Bir öznitelik kaldırma ❓**

  Çoğu durumda, bir öznitelik kaldırma (gibi <xref:System.NonSerializedAttribute>) bölünmesi farklıdır.

## <a name="platform-support"></a>Platform desteği

- **Bir işlem daha önce desteklenmeyen bir platformda destekleyen ✔️**

- **Desteklemenin veya artık bir platformda desteklemiş bir işlem için belirli hizmet paketini gerektiren ❌**

## <a name="internal-implementation-changes"></a>İç uygulama değişiklikleri

- **❓ İç tür'ın yüzey alanını değiştirme**

   Özel yansıma kesintiye olsa da bu tür değişiklikleri genel olarak verilir. Burada popüler üçüncü taraf kitaplıkları veya çok sayıda geliştiriciler, iç API'leri bağlıdır, bazı durumlarda, bu değişikliklere izin verilmiyor.

- **❓ bir üye iç uygulamasını değiştirme**

  Özel yansıma kesintiye olsa da bu değişiklikleri genel olarak verilir. Burada özel yansıma veya değişiklik istenmeyen yan etkileri olduğu tanıtır müşteri kodu sık bağlıdır, bazı durumlarda, bu değişiklikleri izin verilmiyor.

- **✔️ bir işlem performansını iyileştirme**

   Bir işlem performansını değiştirme becerisi gereklidir, ancak bu tür değişiklikler geçerli bir işlem hızına olan kod bozabilir. Bu zaman uyumsuz işlemler zamanlaması üzerinde bağlı olan kod, özellikle geçerlidir. Performans değişikliği diğer söz konusu API'nin davranışını üzerinde hiçbir etkisi olması gerektiğini unutmayın; Aksi takdirde, değişiklik bozucu.

- **✔️ dolaylı olarak (ve genellikle olumsuz) bir işlem performansını değiştirme**

  Bu, söz konusu değişikliğin başka bir nedenle son olarak kategorilere ayrılmamış, kabul edilebilir. Genellikle, gerçekleştirilecek eylemler içir ek işlemleri içerebilir veya yeni işlevler eklemek. Bu, neredeyse her zaman performansını etkiler ancak beklendiği gibi soru işlevinde API'nizi hale getirmek için gerekli olabilir.

- **❌ zaman uyumlu bir API için zaman uyumsuz (ve tersi) değiştirme**

## <a name="code-changes"></a>Kod değişiklikleri

- **✔️ Ekleme [params](../../csharp/language-reference/keywords/params.md) bir parametre**

- **❌ Değiştirme bir [yapı](../../csharp/language-reference/keywords/struct.md) için bir [sınıfı](../../csharp/language-reference/keywords/class.md) ve bunun tersi de geçerlidir**

- **❌ Ekleme [işaretli](../../csharp/language-reference/keywords/virtual.md) kod bloğu için anahtar sözcüğü**

   Bu değişikliği atmak için daha önce yürütülen kodu neden olabilir bir <xref:System.OverflowException> ve kabul edilebilir değil.

- **❌ Kaldırma [params](../../csharp/language-reference/keywords/params.md) bir parametre**

- **❌ olaylar sırasını değiştirme**

  Geliştiricilerin makul olayların aynı sırayla ateşlenmesine bekleyebileceğiniz ve geliştirici kod sık olaylar sıraya göre değişir.

- **Belirli bir eylemi bir olayı tetiklenmeden kaldırma ❌**

- **Olayları verilen sayıda değiştirme ❌ çağırılır**

- **❌ Ekleme <xref:System.FlagsAttribute> bir numaralandırma türü için**
