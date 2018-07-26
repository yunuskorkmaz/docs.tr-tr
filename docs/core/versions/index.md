---
title: .NET core sürüm oluşturma
description: .NET Core sürüm nasıl çalıştığını anlayın.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: aa4f05a1a95c1bfbd16f41ca695ea23d48606772
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792328"
---
# <a name="net-core-versioning"></a>.NET core sürüm oluşturma

.NET core yapılan [NuGet paketlerini](../packages.md), araçları ve çerçeveleri bir birim olarak dağıtılmış. Her biri bu platform katmanları ayrı olarak, daha iyi çevikliği etkinleştirme tutulan olabilir. Bu şekilde önemli sürüm esneklik olsa da de mevcuttur gizliliğinizi korumayı taahhüt eder platform sürümüne ürün anlamak daha kolay hale getirmek için bir birim olarak.

Bu makalede, çalışma zamanı ve .NET Core SDK'sını nasıl belirlendiği açıklığa kavuşturan en amaçlar.

Var. birçok hareketli parçadan bu sürümü bağımsız olarak .NET Core Ancak, .NET Core 2.0 ile başlayarak, yoktur herkes olmasını anlar en üst düzey sürüm numarası anlamak kolay bir *bütün* olarak ".NET Core" sürümü. Bu belgenin geri kalan tüm parçaları sürüm oluşturma işlemlerini ayrıntılarına gider. Bu ayrıntılar, örneğin bir paket yöneticisi değilseniz önemli olabilir.

> [!IMPORTANT]
> Sürüm oluşturma ayrıntıları bu konu başlığında açıklanan, geçerli çalışma zamanı ve .NET Core SDK'sı sürümü için geçerli değildir.
> Sürüm şeması, gelecek sürümlerde değişiyor. En geçerli teklif gördüğünüz [dotnet/tasarımları](https://github.com/dotnet/designs/pull/29) depo.

## <a name="versioning-details"></a>Sürüm oluşturma ayrıntıları

.NET Core 2.0 ile yüklemeleri dosya adında tek sürüm numarasını gösterir. Aşağıdaki sürüm numaralarını birleşik:

* Paylaşılan çerçeve ve ilişkili çalışma zamanı.
* İlişkili .NET Core CLI ve .NET Core SDK'sı.
* `Microsoft.NETCore.App` Metapackage.

Bir üretim ortamı sağlamak için zaman söz konusu olduğunda tek sürüm numarası yapar kullanımını hangi sürümünün kendi geliştirme makinelerinde yüklemek için SDK'ın ve ilgili sürümü paylaşılan framework'ün bilmek, kullanıcılar için daha kolay bir değer olmalıdır. Bir SDK ya da çalışma zamanı indirirken gördüğünüz sürüm numarası aynı zordur.

### <a name="version-selection"></a>Sürüm seçimi

.NET core SDK ve .NET Core çalışma zamanının hangi sürümlerinin çeşitli senaryolarda kullanılır belirleyen ilkeler kümesini uygular. Bu senaryolar ve ilkeleri tam olarak makalesinde üzerinde incelenmektedir [sürüm seçimi](selection.md).

Bu ilkeler, aşağıdaki rolleri gerçekleştirmek olarak düşünebilirsiniz:

* Kolay ve etkili güvenlik ve güvenilirlik güncelleştirmeleri dahil olmak üzere, .NET Core dağıtımı etkinleştirin.
* En son araçları ve komutları hedef çalışma zamanı bağımsız geliştiriciler etkinleştirin.

### <a name="installers"></a>Yükleyicileri

İçin .NET Core 2.0 ile yüklemeler [günlük oluşturur](https://github.com/dotnet/core-setup#daily-builds) ve [serbest](https://www.microsoft.com/net/download/core) anlamak daha kolay olan yeni bir adlandırma düzeni için uygun.
Bu indirmeler yükleyicisi kullanıcı arabirimini de açıkça adları ve yüklü bileşenlerin sürümlerini sunmak için değiştirildi. Özellikle, başlıklar artık indirme ait dosya adında sürüm numarasını gösterir.

#### <a name="file-name-format"></a>Dosya adı biçimi

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Bu biçim bazı örnekleri aşağıda verilmiştir:

```
dotnet-runtime-2.0.4-osx.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-linux-x64.tar.gz                 # Linux binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb            # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb         # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb             # SDK tools
```

Biçim okunabilir ve net bir şekilde ne işiniz gösterilmektedir indirdikten, hangi sürümünün olduğu ve burada kullanabilirsiniz. Çalışma zamanı paketi adını içeren `runtime`, ve SDK'sı içerir `SDK`.

#### <a name="ui-string-format"></a>UI dize biçimi

Tüm web sitesi açıklamaları ve yükleyiciler kullanıcı Arabirimi dizeleri tutarlı, doğru ve basit tutulur. Aşağıdaki tablo bazı örnekler gösterilmektedir:

| Installer | Pencere Başlığı                          | Diğer İçerik Yükleyicisi | Yüklenenler                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | .NET core 2.0 SDK'sı (x 64) Yükleyici     | 2.0.4 .NET core SDK'sı        | .NET core 2.0.4 araçları + .NET Core 2.0.4 çalışma zamanı |
| Çalışma zamanı   | .NET core 2.0 çalışma zamanı (x64) Yükleyici | .NET core 2.0.4 çalışma zamanı    | .NET core 2.0.4 çalışma zamanı                         |

Önizleme sürümleri yalnızca biraz farklılık gösterir:

| Installer | Pencere Başlığı                                    | Diğer İçerik Yükleyicisi        | Yüklenenler                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | .NET core 2.0 Preview 1 (x 64) SDK'sı yükleyicisi     | .NET core 2.0.0 Önizleme 1 SDK'sı     | .NET core 2.0.0 Önizleme 1 araçları + .NET Core 2.0.0 1 çalışma zamanı Önizleme |
| Çalışma zamanı   | .NET core 2.0 Preview 1 çalışma zamanı (x64) Yükleyici | .NET core 2.0.0 Önizleme 1 çalışma zamanı | .NET core 2.0.0 Önizleme 1 çalışma zamanı                                   |

SDK sürümü birden fazla çalışma zamanı sürümünü içeren oluşabilir. Bu durum oluştuğunda, yükleyici UX aşağıdaki gibi (SDK sürümü gösterilir ve yüklü çalışma zamanı sürümleri, Windows ve Mac'te yükleme işleminin sonunda bir Özet sayfasında gösterilir yalnızca) görünür:

| Installer | Pencere Başlığı                      | Diğer İçerik Yükleyicisi                                   | Yüklenenler                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | .NET core 2.1 (x 64) SDK'sı yükleyicisi | 2.1.1 .NET core SDK'sı <br> .NET core 2.1.1 çalışma zamanı <br> .NET core 2.0.6 çalışma zamanı | .NET core 2.1.1 araçları, .NET Core 2.1.1 çalışma zamanı + .NET Core 2.0.6 çalışma zamanı |

.NET Core Araçları çalışma zamanı değişiklikleri güncelleştirilmesi gerektiğini mümkündür. Bu durumda SDK sürümü (örneğin, 2.1.2'yi) artırılır ve ardından çalışma zamanının sonraki zaman zaman verilir (örneğin, teslim tarihi çalışma zamanını ve SDK'sı 2.1.3 sonraki sürede) yakalar.

### <a name="package-managers"></a>Paket yöneticileri

.NET core, Microsoft daha diğer varlıklar tarafından dağıtılabilir. Özellikle, Linux dağıtım sahipleri ve paket maintainers paket yöneticilerinin .NET Core paketleri ekleyebilir. Adlandırılmış ve tutulan bu paketleri nasıl olması gerektiğini ilişkin öneriler için bkz. [.NET Core dağıtımı paketleme](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>En az bir paket kümesi

* `dotnet-runtime-[major].[minor]`: bir çalışma zamanı (yalnızca en son düzeltme eki sürümü bir belirli ana + ikincil birleşimi olmalıdır Paket Yöneticisi'nde kullanılabilir) belirtilen sürüme sahip. Yeni bir düzeltme eki sürümleri güncelleştirme paketi, ancak yeni küçük veya büyük ayrı paketler sürümleridir.

  **Bağımlılıkları**: `dotnet-host`

* `dotnet-sdk`: en son SDK'sı. `update` pay ana, alt, iletme ve sürümleri düzeltme eki.

  **Bağımlılıkları**: en son `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: SDK'sı ile belirtilen sürümü. Böylece kullanıcıların paylaşılan bir çerçeve için SDK kolayca ilişkilendirebilirsiniz belirtilen sürümden yüksek dahil dahil paylaşılan çerçeveleri sürümüdür. Yeni bir düzeltme eki sürümleri güncelleştirme paketi, ancak yeni küçük veya büyük ayrı paketler sürümleridir.

  **Bağımlılıkları**: `dotnet-host`, bir veya daha fazla `dotnet-runtime-[major].[minor]` (bunların kullanılan SDK kodun kendisi, diğerleri burada oluşturup karşı çalıştırmak kullanıcıları içindir).

* `dotnet-host`: en son ana bilgisayar.

##### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme sürümleri çalışma zamanını ve SDK'sını içerecek şekilde karar verebilirsiniz. Bu önizleme sürümleri sürüm bilgisi olmayan içermez `dotnet-sdk` paket, ancak bunları olarak tutulan paketleri ile sürümünden adı birincil ve ikincil sürüm bölümlerini eklenmiş bir ek Önizleme işaretçisi. Örneğin, olabilir bir `dotnet-sdk-2.0-preview1-final` paket.

### <a name="docker"></a>Docker

Adlandırma kuralı genel bir Docker tag bileşen adından önce sürüm numarasını yerleştirmektir. Bu kural, kullanılacak devam edebilir. Geçerli etiketler yalnızca çalışma zamanı sürümü aşağıdaki şekilde ekleyin.

* 1.0.8-Runtime
* 1.0.8-SDK
* 2.0.4-Runtime
* 2.0.4-SDK
* 2.1.1-Runtime
* 2.1.1-sdk

SDK'sı etiketleri, çalışma zamanı yerine SDK sürümü temsil etmek üzere güncelleştirilmelidir.

.NET Core CLI Araçları (SDK'sına dahil), ancak mevcut bir çalışma zamanı ile reship giderilen mümkündür. Bu durumda SDK sürümü (örneğin, 2.1.2'yi) artırılır ve ardından çalışma zamanının sonraki zaman zaman verilir (örneğin, teslim tarihi çalışma zamanını ve SDK'sı 2.1.3 Aşağıdaki sürede) yakalar.

## <a name="semantic-versioning"></a>Semantic Versioning

.NET core kullanan [Semantic Versioning (SemVer)](http://semver.org/), kullanımını benimseyen `MAJOR.MINOR.PATCH` sürüm oluşturma, derece ve değişiklik türünü tanımlamak için sürüm numarasını çeşitli bölümlerini kullanarak.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` bölümleri hiçbir zaman desteklenen sürümleri parçasıdır ve yalnızca gecelik derlemeler, kaynak hedefler, yerel yapılar üzerinde mevcut ve desteklenmeyen Önizleme sürümleri.

### <a name="how-version-numbers-are-incremented"></a>Sürüm numaraları nasıl artırılır?

`MAJOR` ne zaman artırılır:

- Eski bir sürümü artık desteklenmiyor.
- Daha yeni bir `MAJOR` mevcut bir bağımlılık sürümünü benimsenen.
- "Kapalı '." uyumluluk quirk varsayılan ayarı değiştirildi

`MINOR` ne zaman artırılır:

- Genel API yüzey alanı eklenir.
- Yeni bir davranış eklenir.
- Daha yeni bir `MINOR` mevcut bir bağımlılık sürümünü benimsenen.
- Yeni bir bağımlılık kullanıma sunulmuştur.

`PATCH` ne zaman artırılır:

- Hata düzeltmeleri yapılır.
- Daha yeni bir platform için destek eklendi.
- Daha yeni bir `PATCH` mevcut bir bağımlılık sürümünü benimsenen.
- Herhangi bir değişiklik önceki durumlarından biri sığmıyor.

Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en yüksek öğeden artırılır ve aşağıdaki sorguyu sıfırlanır. Örneğin, `MAJOR` artırılır, `MINOR` ve `PATCH` sıfırlanır. Zaman `MINOR` artırılır, `PATCH` sıfır while sıfırlama `MAJOR` dokunulmadan olduğu.

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümlerine sahip bir `-preview[number]-([build]|"final")` sürümüne eklenmiş. Örneğin, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Sürüm hizmet verme

Bir yayın, yayın dalları genellikle geçtikten sonra oluşturmayı durdur günlük oluşturur ve bunun yerine hizmet yapıları üretme başlatın. Bakım sürümlerde bir `-servicing-[number]` sürümüne eklenmiş. Örneğin, `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS geçerli karşılaştırması

.NET Core için sürümlerin iki trenler vardır: uzun süreli destek (LTS) ve geçerli. Kararlılık ve yeni özellikler, yine de destek almaya çalışırken istedikleri düzeyini seçmelerini sağlar.

- LTS, yeni özellikleri daha az sıklıkta Al, ancak daha olgun bir platforma sahip olduğunuz anlamına gelir. LTS, daha uzun bir süre için destek de vardır.
- Geçerli yeni özellikler ve API'ler daha sık alabilirsiniz, ama dezavantajı, güncelleştirmeleri ve bu güncelleştirmeleri daha kısa bir pencerenin sorun daha sık olduğunu olduğu anlamına gelir. Geçerli da tam olarak desteklenir, ancak LTS destek süresi kısadır.

"Geçerli" sürümü için LTS yükseltilen.

"LTS" ve "Geçerli" biz ilişkili destek düzeyini hakkında bir deyim yapmak için belirli sürümler yerleştirin etiket olarak kabul edilmelidir.

Daha fazla bilgi için [.NET Core destek yaşam döngüsü bilgi sayfası](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Sürüm oluşturma düzeni ayrıntıları

.NET core, aşağıdaki bölümleri yapılır:

- Bir konak: ya da *dotnet.exe* framework bağımlı uygulamalar için veya  *\<uygulamaadı > .exe* kendi içindeki uygulamaları için.
- Bir SDK (araçları gerekli Geliştirici makinesinde, ancak üretim kümesi).
- Bir çalışma zamanı.
- Paket olarak dağıtılan bir paylaşılan framework uygulaması. Her bağımsız olarak, özellikle düzeltme eki sürümü oluşturma için sürümü tutulan paketidir.
- İsteğe bağlı olarak, bir dizi [meta paketler](../packages.md) tutulan bir birim olarak hassas paketleri başvuru. Meta paketler paketten ayrı ayrı tutulan olabilir.

.NET core, hedef çerçeve kümesi de içerir (örneğin, `netstandard` veya `netcoreapp`) giderek büyüyen bir API kümesini temsil eden sürüm numaraları artırılır gibi.

### <a name="net-standard"></a>.NET standard

.NET standard kullanarak bir `MAJOR.MINOR` sürüm oluşturma düzeni. `PATCH` düzeyi üzerinde daha az sıklıkta çalışmalar ve sürüm oluşturma için aynı gereksinimleri gerçek bir uygulama olarak mevcut olmayan sözleşmeler kümesini ifade .NET Standard için yararlı değildir.

.NET Standard ve .NET Core sürümleri arasında gerçek hiçbir bağlantısı yoktur: .NET Standard 2.0 uygulamak için .NET Core 2.0 olur, ancak gelecekteki .NET Core sürümleri aynı .NET Standard sürümü için eşler bir garanti yoktur. .NET core, .NET Standard tarafından tanımlanmayan ve bu nedenle, yeni sürümleri yeni bir .NET Standard gerek kalmadan gönderin API'leri sevk edebilir. .NET Core ile çakıştığı için en başından oldu bile .NET standard ayrıca .NET Framework veya Mono, gibi diğer hedeflere uygulayan bir kavramdır.

### <a name="packages"></a>Paketler

Kitaplığı paketlerinin evrim geçiren ve sürüm bağımsız olarak. .NET Framework System ile üst üste paketler. \* derlemeler genellikle 4.x sürümleri, .NET Framework 4.x sürüm oluşturma (geçmişe dönük bir seçim) hizalama kullanır. .NET Framework kitaplıkları ile çakışmaması paketleri (örneğin, [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) genellikle 1.0 başlatmak ve buradan artırın.

Tarafından açıklanan paketleri [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) özel platform tabanına olması nedeniyle kabul edilir.

`NETStandard.Library` Bunlar uygulama düzeyinde aralarındaki bağımlılıkları olduğundan paketleri, genellikle sürümü bir kümesi olarak görüntüler.

### <a name="metapackages"></a>Meta paketler

.NET Core meta paketler için sürüm oluşturma, bir parçası olduklarından .NET Core sürümünde temel alır.

Örneğin, .NET core'da 2.1.3 meta paketler tüm 2.1 olarak sahip gereken kendi `MAJOR` ve `MINOR` sürüm numaraları.

Tüm başvurulan paketlerde her güncelleştirildiğinde metapackage için düzeltme eki sürümü artırılır. Düzeltme eki sürümleri güncel framework sürümünü içermez. Kendi sürüm oluşturma düzeni, temel alınan paketleri değişiklik ancak öncelikle, API düzeyi derecesini temsil etmez, çünkü sonuç olarak, meta paketler kesinlikle SemVer uyumlu değildir.

Şu anda .NET Core için iki birincil meta paketler vardır:

**Microsoft.NETCore.App**

- V1.0 itibariyle .NET Core 1.0 (Bu sürümlerinin eşleştiğinden).
- Eşlendiği `netcoreapp` framework.
- .NET Core dağıtım paketleri açıklar.

Not: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) öncesi .NET standart .NET uygulaması ile uyumluluk sağlamak için var olan başka bir .NET Core metapackage olduğu. Belirli bir çerçeve için bu nedenle eşlemiyor, bir paket sürümleri ister.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) parçası olan kitaplıkları açıklar [.NET Standard](../../standard/library.md). .NET standart, .NET Framework, .NET Core ve Mono gibi destekleyen tüm .NET uygulamaları için geçerlidir.

### <a name="target-frameworks"></a>Hedef Çerçeve

Hedef framework sürümü, yeni API'leri eklendiğinde güncelleştirilir. API şekli ve değil uygulama konuları temsil ettiğinden düzeltme eki sürümü kavramı sahiptirler. Büyük ve küçük sürüm daha önce belirtilen SemVer kurallara ve ile örtüşür `MAJOR` ve `MINOR` uygulamadan .NET Core dağıtımların sayısı.

## <a name="versioning-in-practice"></a>Uygulamada sürüm oluşturma

.NET Core indirdiğinizde, indirilen dosya adını sürümünü, örneğin, taşır `dotnet-sdk-2.0.4-win10-x64.exe`.

İşleme ve günlük olarak, github'da .NET Core depoları üzerinde çekme istekleri yeni sonuçta pek çok kitaplıklarını oluşturur. .NET Core ortak yeni sürümleri her değişiklik için pratik değildir. Bunun yerine, değişiklikleri (örneğin, haftalar veya aylar) yeni bir ortak kararlı .NET Core sürüm yapmadan önce zaman belirsiz bir süre boyunca toplanır.

.NET Core yeni bir sürümü birkaç şey anlamına gelebilir:

- Paketler ve meta paketler yeni sürümleri.
- Yeni sürümler çeşitli çerçevesini, yeni API'leri eklenmesini varsayılıyor.
- .NET Core dağıtımı yeni sürümü.

### <a name="shipping-a-patch-release"></a>Sevkiyat bir düzeltme eki sürümü

.NET Core, büyük bir sürümü gibi sürüm 2.0.0, sevkiyat sonra hataları düzeltin ve performans ve güvenilirlik geliştirmek için .NET Core kitaplıkları için düzeltme eki düzeyi değişiklik yapılmaz. Yeni API sunulan anlamına gelir. Çeşitli meta paketler, güncelleştirilmiş .NET Core kitaplığı paketlerinin başvuracak şekilde güncelleştirilir. Düzeltme eki güncelleştirmeler olarak tutulan meta paketler (`MAJOR.MINOR.PATCH`). Hedef Çerçeve, düzeltme eki sürümleri bir parçası olarak hiçbir zaman güncelleştirilir. Yeni bir .NET Core dağıtımı, eşleşen bir sürüm numarası ile serbest `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-minor-release"></a>Alt sürüm aktarma

.NET Core sürümüyle bir artımlı sevkiyat sonra `MAJOR` sürüm numarası, yeni API'leri, .NET Core kitaplıklara yeni senaryoları etkinleştirmek için eklenir. Çeşitli meta paketler, güncelleştirilmiş .NET Core kitaplığı paketlerinin başvuracak şekilde güncelleştirilir. Düzeltme eki güncelleştirmeleriyle olarak meta paketler belirlendiği `MAJOR` ve `MINOR` alanında yeni framework sürümünün eşleşen sürüm numaraları. Yeni hedef framework adları yeni `MAJOR.MINOR` sürümü, yeni API'leri açıklamak için eklenir (örneğin, `netcoreapp2.1`). Yeni bir .NET Core dağıtımı için eşleşen bir sürüm numarası ile birlikte yayınlanan `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-major-release"></a>Bir ana yayın aktarma

.NET Core, yeni bir ana sürüm birlikte gelen her gönderinin `MAJOR` sürüm numarası artırılır ve `MINOR` sürüm numarası, sıfır olarak sıfırlama. Yeni sürümle önceki ana sürüm sonra ikincil sürümleri tarafından eklenen en az tüm API'leri içerir. Yeni bir ana sürüm önemli yeni senaryolar etkinleştirmeniz gerekir ve eski bir platform desteği düşebilir.

Çeşitli meta paketler, güncelleştirilmiş .NET Core kitaplığı paketlerinin başvuracak şekilde güncelleştirilir. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Metapackage ve `netcore` hedef çerçeve olarak önemli güncelleştirme eşleşen tutulan `MAJOR` yeni sürümünün sürüm numarası.

## <a name="see-also"></a>Ayrıca bkz.

[Hedef çerçeveler](../../standard/frameworks.md)  
[.NET Core dağıtımı paketleme](../build/distribution-packaging.md)  
[.NET core destek yaşam döngüsü bilgi sayfası](https://www.microsoft.com/net/core/support)  
[.NET core 2 + sürüm bağlama](https://github.com/dotnet/designs/issues/3)  
