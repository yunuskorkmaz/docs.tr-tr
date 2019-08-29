---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: 5d23147c8a38fbeea9e88c0a18e1f220e854fec1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105411"
---
# <a name="net-core-distribution-packaging"></a>.NET Core dağıtımı paketleme

.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur. Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir. Bu makale, şu kullanıcılar için yararlıdır:

- Kaynaktan .NET Core oluşturmaya çalışılıyor.
- .NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:

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

- (1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin. Ana bilgisayar yerel bir yürütülebilir dosyadır (`dotnet.exe`).

Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur. Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.

- (2) **Host/FXR/\<FXR sürümü >** ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir. Ana bilgisayar, yüklü en son hostfxr 'yi kullanır. Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur. Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır. Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.

- (3) SDK **/\<SDK sürümü >** SDK ("araç oluşturma" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir. SDK, .NET Core komut satırı arabirimi (CLı), yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevleri ile hedefleri, NuGet, yeni proje şablonları vb. içerir.

- (4) **SDK/nugetfallbackfolder** , veya `dotnet restore` `dotnet build /t:Restore`çalıştırılırken olduğu gibi, geri yükleme işlemi sırasında bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir.

**Paylaşılan** klasör çerçeveler içerir. Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.

- (5) **paylaşılan/Microsoft. netcore. app/\<Runtime sürümü >** bu çerçeve .NET Core çalışma zamanı ve yönetilen kitaplıkları destekler.

- (6, 7) **paylaşılan/Microsoft. AspNetCore. { App, All}/\<aspnetcore sürüm >** ASP.NET Core kitaplıklarını içerir. Altındaki `Microsoft.AspNetCore.App` kitaplıklar, .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir. Altındaki `Microsoft.AspNetCore.All` kitaplıklar, üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.

- (8) **LICENSE. txt, üçüncü taraf bildirimleri. txt** , .NET Core 'un sırasıyla kullanıldığı üçüncü taraf kitaplıkların .NET Core lisansı ve lisanslarıdır.

- (9, 10) **DotNet. 1. gz, DotNet** `dotnet.1.gz` , DotNet el ile yapılan bir sayfasıdır. `dotnet`, DotNet konağının (1) bir symbağlantıdır. Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.

## <a name="recommended-packages"></a>Önerilen paketler

.NET Core sürümü oluşturma çalışma zamanı bileşen `[major].[minor]` sürüm numaralarına dayalıdır.
SDK sürümü aynı `[major].[minor]` kullanır ve SDK için özellik ve düzeltme `[patch]` eki semantiğini birleştiren bir bağımsız içerir.
Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür. Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](../versions/index.md).

Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir. Bu, belirli bir sürümü yüklemenize olanak sağlar.
Sürümün geri kalanı sürüm adına dahil değildir. Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme). Desteklenen paket yöneticileri Linux 'a özgüdür.

Aşağıdaki tabloda önerilen paketler gösterilmektedir:

| Ad                                    | Örnek                | Kullanım durumu: Yüklemesi...           | İçerir           | Bağımlılıklar                                   | Sürüm            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Çalışma zamanı için en son SDK    |                    | DotNet-SDK-[birincil]. [latestminor]               | \<SDK sürüm >     |
| DotNet-SDK-[birincil]. Bazı              | DotNet-SDK-2,1         | Belirli çalışma zamanı için en son SDK |                    | DotNet-SDK-[birincil]. [ikincil]. [en son SDK feat] xx | \<SDK sürüm >     |
| DotNet-SDK-[birincil]. [ikincil]. [SDK feat] xx | DotNet-SDK-2.1.3 xx     | Belirli SDK özelliği sürümü    | (3), (4)            | aspnetcore-Runtime-[ana]. Bazı             | \<SDK sürüm >     |
| aspnetcore-Runtime-[ana]. Bazı      | aspnetcore-Runtime-2,1 | Belirli ASP.NET Core çalışma zamanı   | (6),[(7)]          | DotNet-çalışma zamanı-[birincil]. Bazı                 | \<çalışma zamanı sürüm > |
| DotNet-çalışma zamanı-[birincil]. Bazı          | DotNet-çalışma zamanı-2,1     | Belirli çalışma zamanı                | (5)                | Host-FXR:\<çalışma zamanı sürüm > +                   | \<çalışma zamanı sürüm > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _bağımlılık_                    | (2)                | Ana bilgisayar\<: çalışma zamanı sürümü > +                       | \<çalışma zamanı sürüm > |
| DotNet-konak                             | DotNet-konak            | _bağımlılık_                    | (1), (8), (9), (10)   |                                                | \<çalışma zamanı sürüm > |

Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir. Bu, paketlere bazı etkileri vardır:

- Altındaki `shared/Microsoft.AspNetCore.All` üçüncü taraf kitaplıkları kaynaktan kolayca derlenebilir. Bu nedenle, bu klasör `aspnetcore-runtime` paketten çıkarılır.

- , `NuGetFallbackFolder` Öğesinden`nuget.org`ikili yapıtlar kullanılarak doldurulur. Boş kalmalıdır.

Birden `dotnet-sdk` çok paket `NuGetFallbackFolder`için aynı dosyaları sağlayabilir. Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).

### <a name="preview-versions"></a>Önizleme sürümleri

Paket bakım yapanlar, paylaşılan çerçeve ve SDK 'nın önizleme sürümlerini sağlamaya karar verebilir. Önizleme yayınları `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, veya `dotnet-runtime-[major].[minor]` paketleri kullanılarak sağlanmış olabilir. Önizleme sürümleri için, paket sürümünün birincil sürümü sıfır olarak ayarlanmalıdır. Bu şekilde, son sürüm paketin yükseltmesi olarak yüklenir.

### <a name="patch-packages"></a>Düzeltme eki paketleri

Paketin bir düzeltme eki sürümü bir değişikliğe neden olabileceğinden, bir paket bakımcı _düzeltme eki paketleri_sağlamak isteyebilir. Bu paketler, otomatik olarak yükseltilmeyen belirli bir düzeltme eki sürümünü yüklemenize izin verir. Yalnızca (güvenlik) düzeltmeleriyle yükseltilmeyen nadir koşullarda yama paketlerini kullanın.

Aşağıdaki tabloda önerilen paketler ve **düzeltme eki paketleri**gösterilmektedir:

| Ad                                           | Örnek                  | İçerir         | Bağımlılıklar                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet-SDK-[birincil]. [en son SDK Minor]                     |
| DotNet-SDK-[birincil]. Bazı                     | DotNet-SDK-2,1           |                  | DotNet-SDK-[birincil]. [ikincil]. [en son SDK feat] xx            |
| DotNet-SDK-[birincil]. [ikincil]. [SDK feat] xx        | DotNet-SDK-2.1.3 xx       |                  | DotNet-SDK-[birincil]. [ikincil]. [en son SDK düzeltme eki]             |
| **DotNet-SDK-[birincil]. [ikincil]. düzeltmesi**         | DotNet-SDK-2.1.300       | (3), (4)          | aspnetcore-Runtime-[ana]. [ikincil]. [SDK çalışma zamanı düzeltme eki]    |
| aspnetcore-Runtime-[ana]. Bazı             | aspnetcore-Runtime-2,1   |                  | aspnetcore-Runtime-[ana]. [ikincil]. [son çalışma zamanı düzeltme eki] |
| **aspnetcore-Runtime-[ana]. [ikincil]. düzeltmesi** | aspnetcore-Runtime-2.1.0 | (6),[(7)]        | DotNet-çalışma zamanı-[birincil]. [ikincil]. düzeltmesi                    |
| DotNet-çalışma zamanı-[birincil]. Bazı                 | DotNet-çalışma zamanı-2,1       |                  | DotNet-çalışma zamanı-[birincil]. [ikincil]. [son çalışma zamanı düzeltme eki]     |
| **DotNet-çalışma zamanı-[birincil]. [ikincil]. düzeltmesi**     | DotNet-Runtime-2.1.0     | (5)              | Host-FXR:\<çalışma zamanı sürüm > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | Ana bilgisayar\<: çalışma zamanı sürümü > +                                  |
| DotNet-konak                                    | DotNet-konak              | (1), (8), (9), (10) |                                                           |

Düzeltme Eki paketlerinin kullanılmasına bir alternatif, Paket Yöneticisi 'ni kullanarak paketleri belirli bir sürüme sabitleyebilir. Diğer uygulamaları/kullanıcıları etkilememek için, bu tür uygulamalar bir kapsayıcıda oluşturulup dağıtılabilir.

## <a name="building-packages"></a>Paket oluşturma

[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar. Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.
