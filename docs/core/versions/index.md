---
title: .NET core sürüm oluşturma
description: .NET Core sürüm nasıl çalıştığını anlayın.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: 0cfd620d2b6e6e60531b0e2aa938c1ed64b6af23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-versioning"></a>.NET core sürüm oluşturma

.NET core yapıldığında [NuGet paketlerini](../packages.md), Araçlar ve bir birim olarak dağıtılmış çerçeveleri. Her biri bu platform katmanları ayrı olarak, daha iyi çeviklik etkinleştirme sürümlü olabilir. Bu şekilde önemli sürüm esneklik durumdayken var. Ayrıca bir teknoloji platformu sürümüne ürün anlamak daha kolay hale getirmek için bir birim olarak

Bu makalede, .NET Core SDK ve çalışma zamanı nasıl belirlendiği açıklığa kavuşturan en amaçlar.

Vardır hareketli parça çok sayıda sürümünün bağımsız olarak .NET Core. Ancak, .NET Core 2.0 ile başlayarak, yoktur herkes olmasını anlar en üst düzey sürüm numarası anlamak kolay bir *bütün* olarak ".NET Core" sürümü. Bu belgenin kalan tüm parçaları sürüm ayrıntıları gider. Bu ayrıntılar, örneğin bir paket Yöneticisi iseniz önemli olabilir.

> [!IMPORTANT]
> Bu konuda açıklanan sürüm ayrıntıları .NET Core SDK ve çalışma zamanı geçerli sürümüne uygulanmaz.
> Sürüm düzeni gelecek sürümlerde değiştiriyor. Konumundaki geçerli teklifini görebilirsiniz [dotnet/tasarımları](https://github.com/dotnet/designs/pull/29) deposu.

## <a name="versioning-details"></a>Sürüm oluşturma ayrıntıları

.NET Core 2.0 ile yüklemeler dosya adında tek sürüm numarasını gösterir. Aşağıdaki sürüm numaralarını birleşik:

* Paylaşılan framework ve ilişkili çalışma zamanı.
* .NET Core SDK ve ilişkili .NET Core CLI.
* `Microsoft.NETCore.App` Metapackage.

Bir üretim ortamı sağlamak için zamanı geldiğinde tek sürüm numarası yapar kullanımını SDK'sı Geliştirici makinelerinde yüklemek için hangi sürümü ve hangi karşılık gelen paylaşılan framework sürümünü bilmek kullanıcılar için daha kolay olmalıdır. Bir SDK veya çalışma zamanı indirirken gördüğünüz sürüm numarası aynı olduğu olacak.

### <a name="installers"></a>Yükleyicileri

İçin .NET Core 2.0 ile yüklemeler [günlük derlemeler](https://github.com/dotnet/core-setup#daily-builds) ve [serbest](https://www.microsoft.com/net/download/core) anlamak daha kolay olan yeni bir adlandırma şeması için uygun.
Bu indirmeleri UI yükleyicisinde açıkça adları ve yüklenen bileşenlerin sürümlerini sunmak için de değiştirildi. Özellikle, başlıkları şimdi indirme ait dosya adı aynı sürüm numarasını gösterir.

#### <a name="file-name-format"></a>Dosya adı biçimi

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Bu biçim bazı örnekleri şunlardır:

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

Biçim okunabilir durumdadır ve açıkça ne olduğunuz gösterir indirme, hangi sürümünün olduğu ve burada kullanabilirsiniz. Çalışma zamanı paketi adını içeren `runtime`, ve SDK'sı içerir `SDK`.

#### <a name="ui-string-format"></a>UI dize biçimi

Tüm web sitesi açıklamaları ve yükleyicileri UI dizelerde tutarlı, doğru ve basit tutulur. Aşağıdaki tablo bazı örnekler gösterilmektedir:

| Installer | Pencere Başlığı                          | Yükleyici diğer içeriği | Yüklenenler                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | .NET core 2.0 SDK'sı (x 64) Yükleyici     | .NET core 2.0.4 SDK        | .NET core 2.0.4 araçları + .NET Core 2.0.4 çalışma zamanı |
| Çalışma zamanı   | .NET core 2.0 çalışma zamanı (x64) Yükleyici | .NET core 2.0.4 çalışma zamanı    | .NET core 2.0.4 çalışma zamanı                         |

Önizleme sürümleri yalnızca biraz farklılık gösterir:

| Installer | Pencere Başlığı                                    | Yükleyici diğer içeriği        | Yüklenenler                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | .NET core 2.0 Preview 1 (x 64) SDK'sı yükleyicisi     | .NET core 2.0.0 Önizleme 1 SDK'sı     | .NET core 2.0.0 Preview 1 araçları + .NET Core 2.0.0 1 çalışma zamanı Önizleme |
| Çalışma zamanı   | .NET core 2.0 Preview 1 çalışma zamanı (x64) Yükleyici | .NET core 2.0.0 Preview 1 çalışma zamanı | .NET core 2.0.0 Preview 1 çalışma zamanı                                   |

SDK sürüm çalışma zamanı birden fazla sürümünü içeren oluşabilir. Bu durum oluştuğunda yükleyici UX aşağıdaki gibi yalnızca (SDK sürüm gösterilir ve yüklü çalışma zamanı sürümleri, Windows ve Mac üzerinde yükleme işleminin sonunda Özet sayfasında gösterilir) görünür:

| Installer | Pencere Başlığı                      | Yükleyici diğer içeriği                                   | Yüklenenler                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | .NET core 2.1 (x 64) SDK'sı yükleyicisi | .NET core 2.1.1 SDK <br> .NET core 2.1.1 çalışma zamanı <br> .NET core 2.0.6 çalışma zamanı | .NET core 2.1.1 araçları, .NET Core 2.1.1 çalışma zamanı + .NET Core 2.0.6 çalışma zamanı |

.NET Core Araçları çalışma zamanı değişiklikleri güncelleştirilmesi gerektiğini mümkündür. Bu durumda (örneğin, 2.1.2) SDK sürümü artırılır ve sonra çalışma zamanı sonraki zaman onu gelir (örneğin, hem çalışma zamanı ve SDK 2.1.3 sonraki sürede gönderilen) yakalar.

### <a name="package-managers"></a>Paket Yöneticisi

.NET core Microsoft daha diğer varlıklar tarafından dağıtılabilir. Özellikle, Linux dağıtım sahipleri ve paket maintainers .NET Core paketleri paket yöneticilerinin ekleyebilir. Bu paketleri adlandırılmış ve sürümü tutulan nasıl olmalıdır ilişkin öneriler için bkz: [.NET Core dağıtım paketleme](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Minimum paket ayarlama

* `dotnet-runtime-[major].[minor]`: bir çalışma zamanı (yalnızca en son düzeltme eki sürümü için belirtilen ana + ikincil birlikte olmalıdır Paket Yöneticisi'nde kullanılabilir) belirtilen sürüme sahip. Yeni düzeltme eki sürümleri güncelleştirme paketi, ancak yeni sürümleri küçük veya büyük ayrı paketlerdir.

  **Bağımlılıklar**: `dotnet-host`

* `dotnet-sdk`: en yeni SDK'ya. `update` dökümünü ana, ikincil, iletme ve sürümleri düzeltme eki.

  **Bağımlılıklar**: en son `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: SDK'sı ile belirtilen sürümü. Böylece kullanıcılar için paylaşılan bir çerçeve kolayca bir SDK ilişkilendirebilirsiniz belirtilen sürümden yüksek dahil dahil paylaşılan çerçeveler sürümüdür. Yeni düzeltme eki sürümleri güncelleştirme paketi, ancak yeni sürümleri küçük veya büyük ayrı paketlerdir.

  **Bağımlılıklar**: `dotnet-host`, bir veya daha fazla `dotnet-runtime-[major].[minor]` (bunlardan birini kullanılan SDK kodunun kendisi, diğer kullanıcıların derleyip karşı çalıştırmak İşte).

* `dotnet-host`: son ana bilgisayar.

##### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme sürümleri çalışma zamanı ve SDK'sını içerecek şekilde karar verebilirsiniz. Bu önizleme sürümleri sürüm bilgisi olmayan içerme `dotnet-sdk` paket, ancak yayın bunları olarak sürümlü paketleri adı birincil ve ikincil sürüm bölümlerini eklenmiş bir ek Önizleme işaretçisi ile. Örneğin, olabilir bir `dotnet-sdk-2.0-preview1-final` paketi.

### <a name="docker"></a>Docker

Adlandırma genel bir Docker etiketi bileşen adı önce sürüm numarası yerleştirmektir. Bu kural, kullanılacak devam edebilir. Geçerli etiketler yalnızca çalışma zamanı sürümü aşağıdaki şekilde ekleyin.

* 1.0.8-Runtime
* 1.0.8-SDK
* 2.0.4-Runtime
* 2.0.4-SDK
* 2.1.1-Runtime
* 2.1.1-sdk

Çalışma zamanı yerine SDK sürümü temsil etmek için SDK etiketleri güncelleştirilmesi gerekir.

(SDK'ın dahil) .NET Core CLI araçlarını var olan bir çalışma zamanı reship ancak düzeltilen mümkündür. Bu durumda (örneğin, 2.1.2) SDK sürümü artırılır ve sonra çalışma zamanı sonraki zaman onu gelir (örneğin, hem çalışma zamanı ve SDK 2.1.3 Aşağıdaki sürede gönderilen) yakalar.

## <a name="semantic-versioning"></a>Anlamsal sürüm oluşturma

.NET core kullanan [anlamsal sürüm oluşturma (SemVer)](http://semver.org/), kullanımını benimsenmesi `MAJOR.MINOR.PATCH` derecesini ve değişikliğin türünü tanımlamak için sürüm numarasını çeşitli bölümlerini kullanarak sürüm oluşturma.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` bölümleri desteklenen sürümleri hiçbir zaman parçasıdır ve yalnızca her gece derlemeleri, kaynak hedefleri, yerel yapılar mevcut ve desteklenmeyen Önizleme serbest bırakır.

### <a name="how-version-numbers-are-incremented"></a>Sürüm numaraları nasıl artırılır?

`MAJOR` ne zaman artırılır:

- Eski bir sürümü artık desteklenmiyor.
- Daha yeni bir `MAJOR` mevcut bir bağımlılık sürümü benimsenen.
- Bir uyumluluk quirk varsayılan değerini "kapalı." değiştirildi

`MINOR` ne zaman artırılır:

- Genel API yüzey alanını eklenir.
- Yeni bir davranış eklenir.
- Daha yeni bir `MINOR` mevcut bir bağımlılık sürümü benimsenen.
- Yeni bir bağımlılık sunulmuştur.

`PATCH` ne zaman artırılır:

- Hata düzeltmeleri yapılır.
- Daha yeni bir platform desteği eklendi.
- Daha yeni bir `PATCH` mevcut bir bağımlılık sürümü benimsenen.
- Herhangi bir değişiklik önceki durumlarda birini uygun değil.

Birden fazla değişiklik olduğunda, tek tek değişikliklerinden etkilenen yüksek öğesi artırılır ve aşağıdaki olanları sıfırlanır. Örneğin, `MAJOR` artırılır, `MINOR` ve `PATCH` sıfırlanır. Zaman `MINOR` artırılır, `PATCH` sıfır while sıfırlama `MAJOR` dokunulmadan değil.

### <a name="preview-versions"></a>Önizleme sürümleri

Önizleme sürümlere sahip bir `-preview[number]-([build]|"final")` sürümüne eklenmiş. Örneğin, `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Sürümleri bakım

Bir yayın çıkışı, yayın dalları genellikle göründükten sonra oluşturan Dur günlük oluşturur ve bunun yerine bakım derlemeleri oluşturan başlatın. Bakım sürümlere sahip bir `-servicing-[number]` sürümüne eklenmiş. Örneğin, `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS geçerli karşılaştırması

.NET Core sürümlerin iki trenler vardır: uzun süreli destek (LTS) ve geçerli. Kullanıcıların düzeyi kararlılık hala desteklenmekte olan sırasında istedikleri yeni özellikler ve çekme olanak tanır.

- Yeni özellikler daha az sıklıkta alırsınız, ancak daha da olgun bir platform sahip LTS anlamına gelir. LTS daha uzun bir süre desteği de vardır.
- Geçerli olan yeni özellikleri ve API'leri daha sık alırsınız, ancak dezavantajı, güncelleştirmeleri ve bu güncelleştirmeleri süre daha kısa bir pencere durum daha sık olmasıdır anlamına gelir. Geçerli tam olarak desteklenir, ancak destek süresi LTS kısadır.

"Geçerli" sürüm LTS için yükseltilen.

"LTS" ve "Geçerli" biz ilişkili düzeyde desteği hakkında bir deyim yapmak için belirli sürümlerinde put etiket olarak düşünülmelidir.

Daha fazla bilgi için bkz: [.NET Core destek yaşam döngüsü olgu sayfası](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Sürüm oluşturma düzeni ayrıntıları

.NET core aşağıdaki bölümleri yapılır:

- Bir ana bilgisayar: ya da *dotnet.exe* framework bağımlı uygulamalar için veya  *\<uygulamaadı > .exe* kendi içinde bulunan uygulamalar için.
- Bir SDK (araçları gerekli bir geliştiricinin makinede, ancak üretim kümesi).
- Bir çalışma zamanı.
- Paketler olarak dağıtılmış bir paylaşılan framework uygulaması. Her bağımsız olarak, özellikle düzeltme eki sürüm oluşturma için sürümü tutulan paketidir.
- İsteğe bağlı olarak, bir dizi [metapackages](../packages.md) sürümlü bir birim olarak hassas paketleri başvuru. Metapackages ayrı olarak paketlerinden sürümlü olabilir.

.NET core ayrıca hedef çerçeve kümesini içerir (örneğin, `netstandard` veya `netcoreapp`) giderek daha büyük bir API kümesini temsil eden sürüm numaralarını artırılır gibi.

### <a name="net-standard"></a>.NET standart

.NET standart kullanarak bir `MAJOR.MINOR` sürüm düzeni. `PATCH` Düzey standart .NET için yararlı değildir üzerinde daha az sıklıkta yinelendiğinde ve sürüm oluşturma için gerçek uygulaması ile aynı gereksinimlerini sunmak değil sözleşmeleri kümesini ifade eder.

.NET standart ve .NET Core sürümleri arasında gerçek hiçbir ilişki yok: .NET Core 2.0 gerçekleşir .NET standart 2.0 uygulamak için ancak, .NET Core gelecek sürümlerinde aynı .NET standart sürüme eşler garantisi yoktur. .NET core standart .NET tanımlı değil ve yeni sürümler yeni bir .NET standart gerek kalmadan, bu nedenle sevk API'leri gönderebilirsiniz. .NET Core ile çakıştığı için en başından oldu olsa bile .NET standart de .NET Framework veya Mono, gibi diğer hedefler için geçerli bir kavramdır.

### <a name="packages"></a>Paketler

Kitaplık paketleri gelişmesi ve sürüm bağımsız olarak. .NET Framework sistemi ile üst üste paketler. \* derlemeler genellikle 4.x sürümleri, .NET Framework 4.x sürüm oluşturma (Geçmiş seçim) hizalama kullanın. .NET Framework kitaplıkları ile çakışmaması paketleri (örneğin, [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) genellikle 1.0 başlatın ve buradan artırın.

Tarafından açıklanan paketleri [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) özel platform tabanına olması nedeniyle kabul edilir.

`NETStandard.Library` Uygulama düzeyi bağımlılıkları aralarında olduğundan paketler, genellikle sürüm bir küme olarak görüntüler.

### <a name="metapackages"></a>Metapackages

Sürüm oluşturma için .NET Core metapackages bir parçası olan .NET Core sürümü temel alır.

Örneğin, .NET Core 2.1.3 içinde metapackages tüm 2.1 olarak sahip gerekir kendi `MAJOR` ve `MINOR` sürüm numaraları.

Başvurulan bir paket her güncelleştirildiğinde metapackage için düzeltme eki sürümü artırılır. Düzeltme eki sürümleri güncelleştirilmiş framework sürümü dahil etmeyin. Kendi sürüm düzenini temel alınan paketler değişiklik, ancak öncelikle API düzeyini derece temsil etmez çünkü sonuç olarak, metapackages kesinlikle SemVer uyumlu değil.

Şu anda .NET Core için iki birincil metapackages vardır:

**Microsoft.NETCore.App**

- .NET Core (Bu sürümler eşleşen) 1.0 sürümünden itibaren V1.0.
- Eşlendiği `netcoreapp` framework.
- .NET Core dağıtım paketinde açıklar.

Not: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) .NET öncesi .NET standart uygulaması ile uyumluluk sağlamak için mevcut başka bir .NET Core metapackage olduğu. Belirli bir çerçeve için bu nedenle eşlenmez, sürümleri bir paket ister.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) parçası olan kitaplıkları açıklar [.NET standart](../../standard/library.md). .NET standart, .NET Framework, .NET Core ve Mono gibi destek tüm .NET uygulamaları için geçerlidir.

### <a name="target-frameworks"></a>Hedef Çerçeve

Yeni API eklendiğinde hedef framework sürümlerini güncelleştirilir. API şekli ve değil uygulama sorunları temsil ettiği düzeltme eki sürümü kavramına sahip olurlar. Birincil ve ikincil sürüm daha önce belirtilen SemVer kurallara ve ile örtüşür `MAJOR` ve `MINOR` uygulamadan .NET Core dağıtımların sayısı.

## <a name="versioning-in-practice"></a>Uygulamada sürüm oluşturma

.NET Core yüklediğinizde, indirilen dosya adını sürüm, örneğin, izleme `dotnet-sdk-2.0.4-win10-x64.exe`.

İşlemeleri vardır ve her gün, .NET Core depoları github'da üzerinde çekme istekleri yeni sonuçta birçok kitaplıklarının oluşturur. Yeni ortak sürümlerini .NET Core her değişiklik oluşturmak mümkün değil. Bunun yerine, değişiklikleri bir belirlenmemiş süre boyunca yeni bir ortak kararlı .NET Core sürüm yapmadan önce (örneğin, hafta veya ay) toplanır.

.NET Core yeni bir sürümü birkaç şey anlamına gelebilir:

- Paketler ve metapackages yeni sürümleri.
- Yeni API eklenmesi varsayılarak çeşitli çerçeveleri yeni sürümleri.
- .NET Core dağıtım yeni sürümü.

### <a name="shipping-a-patch-release"></a>Bir düzeltme eki sürümü aktarma

.NET Core sürüm 2.0.0, gibi bir ana yayın sevkiyat sonra hataları düzeltin ve performansı ve güvenilirliği iyileştirmek için .NET Core kitaplıkları için düzeltme eki düzeyi değişiklik yapılmaz. Yeni bir API sunulan anlamına gelir. Çeşitli metapackages güncelleştirilmiş .NET Core kitaplığı paketleri başvurmak için güncelleştirilmiştir. Düzeltme eki güncelleştirmeler olarak metapackages belirlendiği (`MAJOR.MINOR.PATCH`). Bir hedef çerçeveyi düzeltme eki sürümleri bir parçası olarak hiçbir zaman güncelleştirilir. Yeni bir .NET Core dağıtım sürümüyle eşleşen bir sürüm numarası olan yayımlanan `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-minor-release"></a>Bir alt yayın aktarma

.NET Core sürümüyle bir artırılır sevkiyat sonra `MAJOR` sürüm numarası, yeni API'leri, .NET Core kitaplıklara yeni senaryoları etkinleştirmek için eklenir. Çeşitli metapackages güncelleştirilmiş .NET Core kitaplığı paketleri başvurmak için güncelleştirilmiştir. Düzeltme eki güncelleştirmeleriyle olarak metapackages belirlendiği `MAJOR` ve `MINOR` yeni framework sürümü eşleşen sürüm numaraları. Yeni hedef framework adlarıyla yeni `MAJOR.MINOR` sürümü, yeni API'leri açıklamak için eklenir (örneğin, `netcoreapp2.1`). Eşleşen bir sürüm numarası olan yeni bir .NET Core dağıtım yayımlanan `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-major-release"></a>Bir ana yayın aktarma

.NET Core yeni ana sürümüyle birlikte gelen her zaman `MAJOR` sürüm numarasını artar ve `MINOR` sürüm numarası sıfıra sıfırlama. Yeni sürümle önceki ana sürüm sonra ikincil sürümleri tarafından eklenen en az tüm API'leri içerir. Yeni bir ana sürüm önemli yeni senaryolar etkinleştirmeniz gerekir ve daha eski bir platform desteği düşebilir.

Çeşitli metapackages güncelleştirilmiş .NET Core kitaplığı paketleri başvurmak için güncelleştirilmiştir. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Metapackage ve `netcore` hedef çerçeve olarak eşleşen önemli güncelleştirme sürümü tutulan `MAJOR` yeni sürümünün sürüm numarası.

## <a name="see-also"></a>Ayrıca bkz.

[Hedef çerçeveler](../../standard/frameworks.md)  
[.NET Core dağıtımı paketleme](../build/distribution-packaging.md)  
[.NET core destek yaşam döngüsü olgu sayfası](https://www.microsoft.com/net/core/support)  
[.NET core 2 + sürüm bağlama](https://github.com/dotnet/designs/issues/3)  
