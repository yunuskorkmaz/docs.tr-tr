---
title: .NET core dağıtımı paketleme
description: Paketleme hakkında bilgi edinin adı ve sürümü .NET Core dağıtımı.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: b961d84053dc41e75e002c8c12419fdef99ded4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585251"
---
# <a name="net-core-distribution-packaging"></a>.NET core dağıtımı paketleme

.NET Core daha da fazla platformlarda kullanılabilir hale geldiğinde, adı, paket hakkında bilgi edinmek yararlı olur ve sürümü. Bu şekilde, paket maintainers burada .NET çalıştırmak kullanıcıların seçim ne olursa olsun, tutarlı bir deneyim sağlamak yardımcı olabilir. Bu makale, olan kullanıcılar için yararlıdır:

* Kaynaktan .NET Core derleme çalışılıyor.
* Sonuçta elde edilen düzeni veya üretilen paketlerin etkileyebilecek .NET Core CLI değişiklik yapmak isteyen.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core dosya şu şekilde düzenlenmiştir çeşitli bileşenlerden oluşur:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** ana bilgisayar (diğer adıyla "Karıştırıcı") iki ayrı rol yok: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirme ve komutları ona gönderileceği bir SDK'yı etkinleştirin. Konağın yerel yürütülebilir olduğundan (`dotnet.exe`).

Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu tutulan dizinler (2,3,5,6) aittir. Başka bir deyişle, birden çok sürümü yan yana yüklemenizden sistemde olabilir.

- (2) **konak/fxr/\<fxr sürüm >** ana bilgisayar tarafından kullanılan çerçeve çözümlemesi mantığı içerir. Ana bilgisayar yüklü en son hostfxr kullanır. Hostfxr uygun çalışma zamanı seçmek için bir .NET Core uygulaması yürütülürken sorumludur. Örneğin, kullanılabilir olduğunda, .NET Core 2.0.0 kullandığı 2.0.5 çalışma zamanı için yerleşik uygulama. Benzer şekilde, hostfxr uygun SDK'sı, geliştirme sırasında seçer.

- (3) **sdk /\<sdk sürümü >** SDK (diğer adıyla "Araçlar"), yazma ve .NET Core kitaplıkları ve uygulamaları oluşturmak için kullanılan yönetilen araçlar kümesi. SDK'sı, .NET Core komut satırı arabirimi (CLI), yönetilen diller System.codeDom, MSBuild ve ilişkili derleme görevleri ve hedefleri, NuGet, yeni proje şablonları vb. içerir.

- (4) **sdk/NuGetFallbackFolder** NuGet paketlerini geri yükleme işlemi sırasında gibi bir SDK'sı tarafından kullanılan önbelleğini içeren çalıştırırken `dotnet restore` veya `dotnet build /t:Restore`.

**Paylaşılan** klasörü çerçeveleri içerir. Farklı uygulamaları tarafından kullanılabilmesi için merkezi bir konumda bir dizi paylaşılan bir çerçeve sağlar.

- (5) **shared/Microsoft.NETCore.App/\<çalışma zamanı sürümü >** bu framework, .NET Core çalışma zamanı ve yönetilen kütüphanelerinizi destek içerir.

- (6,7) **shared/Microsoft.AspNetCore. { Uygulama, tüm} /\<aspnetcore sürüm >** ASP.NET Core kitaplıkları içerir. Kitaplıklar `Microsoft.AspNetCore.App` geliştirilen ve .NET Core projesinin bir parçası desteklenir. Kitaplıklar `Microsoft.AspNetCore.All` ayrıca üçüncü taraf kitaplıklarını içeren bir üst kümesi olan.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** .NET Core lisans ve üçüncü taraf kitaplıkların sırasıyla'de .NET Core, kullanılan lisansları.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` dotnet el ile sayfasıdır. `dotnet` dotnet host(1) için hedefine sembolik bağlantı olur. Bu dosyalar, sistem tümleştirme için iyi bilinen konumlara yüklenir.

## <a name="recommended-packages"></a>Önerilen paketleri

.NET core sürüm çalışma zamanı bileşeni temel `[major].[minor]` sürüm numaraları.
Aynı SDK sürümünü kullanan `[major].[minor]` ve bağımsız `[patch]` için SDK'sı, özellik ve düzeltme eki semantiği birleştirir.
Örneğin: SDK'sı sürüm 2.2.302 2,2 çalışma zamanını destekleyen SDK'sı üçüncü özelliği sürümünü ikinci düzeltme eki sürümüdür. Sürüm oluşturma nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürüm genel bakış](../versions/index.md).

Bazı paketler, adında sürüm numarasının bölümü içerir. Bu, belirli bir sürümünü yüklemek sağlar.
Rest sürümünün sürüm adı dahil değildir. Bu işletim sistemi Paket Yöneticisi'nin güncelleştirme paketleri (örneğin, güvenlik düzeltmeleri otomatik olarak yükleme) sağlar. Desteklenen paket yöneticilerinin belirli Linux var.

Aşağıdaki tabloda, önerilen paketler gösterilmektedir:

| Ad                                    | Örnek                | Kullanım örneği: Yükle...           | İçerir           | Bağımlılıklar                                   | Sürüm            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Çalışma zamanı ana için en son SDK'sı    |                    | DotNet - sdk-[major]. [latestminor]               | \<SDK sürümü >     |
| DotNet - sdk-[major]. [minor]              | DotNet sdk 2.1         | Belirli bir çalışma zamanı için en son SDK'sı |                    | DotNet - sdk-[major]. [minor]. [en son SDK'sı feat] xx | \<SDK sürümü >     |
| DotNet - sdk-[major]. [minor]. [sdk feat] xx | DotNet sdk 2.1.3xx     | Belirli bir sdk özellik yayını    | (3),(4)            | aspnetcore - çalışma zamanı-[major]. [minor]             | \<SDK sürümü >     |
| aspnetcore - çalışma zamanı-[major]. [minor]      | aspnetcore çalışma zamanı 2.1 | Belirli bir ASP.NET Core çalışma zamanı   | (6),[(7)]          | DotNet - çalışma zamanı-[major]. [minor]                 | \<çalışma zamanı sürüm > |
| DotNet - çalışma zamanı-[major]. [minor]          | DotNet çalışma zamanı 2.1     | Belirli bir çalışma zamanı                | (5)                | konak fxr:\<çalışma zamanı sürümü > +                   | \<çalışma zamanı sürüm > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _Bağımlılık_                    | (2)                | konak:\<çalışma zamanı sürümü > +                       | \<çalışma zamanı sürüm > |
| DotNet-host                             | DotNet-host            | _Bağımlılık_                    | (1),(8),(9),(10)   |                                                | \<çalışma zamanı sürüm > |

Çoğu dağıtımları kaynağından oluşturulacak tüm yapıtlar gerektirir. Bu bazı paketlere etkisi:

- Üçüncü taraf kitaplıklar `shared/Microsoft.AspNetCore.All` kaynaktan kolayca oluşturulamıyor. Bu klasöre gelen atlanmış biçimde `aspnetcore-runtime` paket.

- `NuGetFallbackFolder` İkili yapılardan kullanarak doldurulur `nuget.org`. Boş kalmalıdır.

Birden çok `dotnet-sdk` paketler için de indirdiğiniz dosyaları sağlayabilir `NuGetFallbackFolder`. Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyalar aynı olmalıdır (sağlama toplamı, değiştirilme tarihini ve benzeri).

### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme sürümleri paylaşılan çerçeve ve SDK sağlar karar verebilirsiniz. Önizleme sürümleri kullanılarak sağlanmalıdır `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, veya `dotnet-runtime-[major].[minor]` paketleri. Önizleme sürümleri için ana Paket sürümü sıfır olarak ayarlamanız gerekir. Bu şekilde son sürümü yükseltme paketi olarak yüklenir.

### <a name="patch-packages"></a>Düzeltme eki paketleri

Bir paketin bir düzeltme eki sürümü bozucu bir değişikliğe neden olduğundan, bir paket Bakımcı sağlamak isteyebilirsiniz _paketleri düzeltme eki_. Bu paketleri otomatik olarak yükseltme değilse bir özel düzeltme eki sürümü yüklemek izin verin. Yalnızca Yöneticiler (güvenlik) ile yükseltilmiş düzeltmeleri olmayan eki paketlerini nadir durumlarda kullanın.

Önerilen paketleri aşağıdaki tabloda gösterir ve **paketleri düzeltme eki**:

| Ad                                           | Örnek                  | İçerir         | Bağımlılıklar                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[major]. [küçük en son sdk]                     |
| DotNet - sdk-[major]. [minor]                     | DotNet sdk 2.1           |                  | DotNet - sdk-[major]. [minor]. [en son SDK'sı feat] xx            |
| DotNet - sdk-[major]. [minor]. [sdk feat] xx        | DotNet sdk 2.1.3xx       |                  | DotNet - sdk-[major]. [minor]. [son sdk yolu]             |
| **DotNet - sdk-[major]. [minor]. [düzeltme]**         | DotNet sdk 2.1.300       | (3),(4)          | aspnetcore - çalışma zamanı-[major]. [minor]. [sdk düzeltme çalışma zamanı]    |
| aspnetcore - çalışma zamanı-[major]. [minor]             | aspnetcore çalışma zamanı 2.1   |                  | aspnetcore - çalışma zamanı-[major]. [minor]. [en son düzeltme çalışma zamanı] |
| **aspnetcore - çalışma zamanı-[major]. [minor]. [düzeltme]** | aspnetcore çalışma zamanı 2.1.0 | (6),[(7)]        | DotNet - çalışma zamanı-[major]. [minor]. [düzeltme]                    |
| DotNet - çalışma zamanı-[major]. [minor]                 | DotNet çalışma zamanı 2.1       |                  | DotNet - çalışma zamanı-[major]. [minor]. [en son düzeltme çalışma zamanı]     |
| **DotNet - çalışma zamanı-[major]. [minor]. [düzeltme]**     | DotNet çalışma zamanı 2.1.0     | (5)              | konak fxr:\<çalışma zamanı sürümü > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | konak:\<çalışma zamanı sürümü > +                                  |
| DotNet-host                                    | DotNet-host              | (1),(8),(9),(10) |                                                           |

Düzeltme eki paketleri bir alternatifidir _sabitleme_ Paket Yöneticisi'ni kullanarak belirli bir sürümü için paketleri. Diğer uygulamalar/kullanıcıları etkilemeden önlemek için bu tür uygulamalar oluşturulabilen ve bir kapsayıcıda dağıtılır.

## <a name="building-packages"></a>Yapı paketleri

[Kaynak/dotnet-derleme](https://github.com/dotnet/source-build) depo, bir .NET Core SDK'sını ve tüm bileşenlerinin kaynak tarball derleme hakkında yönergeler sağlar. Kaynak derleme deposu çıktısını bu makalenin ilk bölümünde açıklanan düzenini eşleşir.
