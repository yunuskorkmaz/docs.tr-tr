---
title: .NET Core uygulama dağıtımı
description: .NET Core uygulaması dağıtma yolları hakkında bilgi edinin.
ms.date: 12/03/2018
ms.custom: seodec18
ms.openlocfilehash: fd15d41065b0a6ecb1a0bf04a0f0ab292a0a5fb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089190"
---
# <a name="net-core-application-deployment"></a>.NET Core uygulama dağıtımı

.NET Core uygulamaları için üç tür dağıtım oluşturabilirsiniz:

- Çerçeveye bağımlı dağıtım. Adından da anlaşılacağı gibi, çerçeveye bağımlı dağıtım (FDD), hedef sistemde .NET Core 'un paylaşılan sistem genelindeki bir sürümünün varlığına dayanır. .NET Core zaten mevcut olduğundan, uygulamanız .NET Core yüklemeleri arasında da taşınabilir. Uygulamanız yalnızca kendi kodunu ve .NET Core kitaplıklarının dışında olan üçüncü taraf bağımlılıklarını içerir. FDDs, komut satırından [DotNet yardımcı programını](../tools/dotnet.md) kullanarak başlatılabilen *. dll* dosyaları içerir. Örneğin, `dotnet app.dll` `app`adlı bir uygulamayı çalıştırır.

- Kendi kendine kapsanan dağıtım. FDD 'nin aksine, kendinden bağımsız bir dağıtım (SCD) hedef sistemdeki paylaşılan bileşenlerin varlığına güvenmez. .NET Core kitaplıkları ve .NET Core çalışma zamanı dahil olmak üzere tüm bileşenler, uygulamaya dahildir ve diğer .NET Core uygulamalarından yalıtılmıştır. SCN 'Ler, platforma özgü .NET Core ana bilgisayarının yeniden adlandırılmış bir sürümü olan bir yürütülebilir dosya (`app`adlı bir uygulama için Windows platformlarında *app. exe* gibi) ve gerçek değer olan bir *. dll* dosyası ( *app. dll*gibi) içerir. Uygulamanızı.

- Çerçeveye bağımlı yürütülebilir dosyalar. Hedef platformda çalışan bir yürütülebilir dosya oluşturur. FDDs 'ye benzer şekilde, çerçeveye bağımlı çalıştırılabilirler (FDE) platforma özgüdür ve kendi içinde değildir. Bu dağıtımlar, .NET Core 'un çalışmasına yönelik paylaşılan sistem genelinde bir sürümünün varlığını de temel alır. Bir SCD aksine, uygulamanız yalnızca kodunuzu ve .NET Core kitaplıklarının dışında olan üçüncü taraf bağımlılıklarını içerir. FDEs, hedef platformda çalışan bir yürütülebilir dosya oluşturur.

## <a name="framework-dependent-deployments-fdd"></a>Çerçeveye bağımlı dağıtımlar (FDD)

FDD için yalnızca uygulamanızı ve üçüncü taraf bağımlılıklarını dağıtırsınız. Uygulamanız, hedef sistemde bulunan .NET Core sürümünü kullanacaktır. Bu, .NET Core ve ASP.NET Core .NET Core ' u hedefleyen uygulamalar için varsayılan dağıtım modelidir.

### <a name="why-create-a-framework-dependent-deployment"></a>Neden çerçeveye bağımlı dağıtım oluşturulsun?

FDD dağıtımı, bir dizi avantaja sahiptir:

- .NET Core uygulamanızın önceden çalışacağı hedef işletim sistemlerini tanımlamanız gerekmez. .NET Core, işletim sisteminden bağımsız olarak yürütülebilir dosyalar ve kitaplıklar için ortak bir PE dosya biçimi kullandığından, .NET Core, temel alınan işletim sisteminden bağımsız olarak uygulamanızı yürütebilirler. PE dosya biçimi hakkında daha fazla bilgi için bkz. [.NET derleme dosyası biçimi](../../standard/assembly/file-format.md).

- Dağıtım paketinizin boyutu küçüktür. Uygulamanızı ve bağımlılıklarını yalnızca .NET Core 'u değil, dağıtırsınız.

- Geçersiz kılınmadıkça, FDDs hedef sistemde yüklü olan en son hizmet verilen çalışma zamanını kullanacaktır. Bu, uygulamanızın .NET Core çalışma zamanının en son düzeltme eki yüklenmiş sürümünü kullanmasını sağlar. 

- Birden çok uygulama aynı .NET Core yüklemesini kullanır, bu da konak sistemlerindeki disk alanını ve bellek kullanımını azaltır.

Birkaç dezavantajın de vardır:

- Uygulamanız yalnızca, uygulamanızın hedeflediği .NET Core sürümü [veya daha sonraki bir sürüm](../versions/selection.md#framework-dependent-apps-roll-forward), ana bilgisayar sisteminde zaten yüklüyse çalıştırılabilir.

- .NET Core çalışma zamanı ve kitaplıklarının gelecek sürümlerde bilginiz olmadan değiştirilmesi mümkündür. Nadir durumlarda, bu durum uygulamanızın davranışını değiştirebilir.

## <a name="self-contained-deployments-scd"></a>Kendi içindeki dağıtımlar (SCD)

Kendi kendine kapsanan bir dağıtım için uygulamanızı ve gerekli üçüncü taraf bağımlılıklarını, uygulamayı oluşturmak için kullandığınız .NET Core sürümü ile birlikte dağıtırsınız. SCD oluşturma, çeşitli platformlarda [.NET Core 'un yerel bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) içermez, bu nedenle uygulama çalışmadan önce bunların mevcut olması gerekir. Çalışma zamanında sürüm bağlama hakkında daha fazla bilgi için [.NET Core 'da sürüm bağlama](../versions/selection.md)makalesindeki makaleye bakın.

NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, .NET Core *düzeltme eki sürümü ileri*'yi destekler. Kendi kendine içerilen bir dağıtım oluşturduğunuzda, .NET Core araçları otomatik olarak uygulamanızın hedeflediği .NET Core sürümünün hizmet verilen en son çalışma zamanını içerir. (En son hizmet verilen çalışma zamanı, güvenlik düzeltme eklerini ve diğer hata düzeltmelerini içerir.) Hizmet verilen çalışma zamanının yapı sisteminizde mevcut olması gerekmez; NuGet.org adresinden otomatik olarak indirilir. Düzeltme eki sürümü iletme hakkında yönergeler de dahil olmak üzere daha fazla bilgi için, bkz. [kendi kendine kapsanan dağıtım çalışma zamanı ileri](runtime-patch-selection.md).

FDD ve SCD dağıtımları ayrı ana bilgisayar yürütülebilir dosyaları kullanır, bu nedenle, bir SCD için bir konak çalıştırılabiliri yayımcı imzacıyla imzalayabilirsiniz.

### <a name="why-deploy-a-self-contained-deployment"></a>Neden kendi kendine içerilen bir dağıtım dağıtılır?

Kendi içinde dağıtımı dağıtmak iki önemli avantaja sahiptir:

- Uygulamanızla dağıtılan .NET Core sürümü için tek denetiminiz vardır. .NET Core yalnızca sizin tarafınızdan hizmet verebilir.

- Üzerinde çalışacağı .NET Core sürümünü sağladığından, hedef sistemin .NET Core uygulamanızı çalıştıracağından emin olabilirsiniz.

Ayrıca çeşitli dezavantajlara sahiptir:

- .NET Core dağıtım paketinize eklendiğinden, dağıtım paketlerini önceden oluşturduğunuz hedef platformları seçmeniz gerekir.

- .NET Core 'un yanı sıra uygulamanızı ve üçüncü taraf bağımlılıklarını da dahil etmeniz gerektiğinden, dağıtım paketinizin boyutu nispeten büyük olur.

  .NET Core 2,0 ile başlayarak, .NET Core [*Genelleştirme sabit modunu*](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)kullanarak Linux sistemlerinde dağıtımınızın boyutunu YAKLAŞıK 28 MB azaltabilirsiniz. Normalde, Linux üzerinde .NET Core, genelleştirme desteği için [ICU kitaplıklarını](http://icu-project.org) kullanır. Sabit modda, kitaplıklar dağıtımınıza dahil edilmez ve tüm kültürler [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)gibi davranır.

- Birçok bağımsız .NET Core uygulamasını bir sisteme dağıtmak, her uygulama .NET Core dosyalarını yinelemediğinden önemli miktarda disk alanı tüketebilir.

## <a name="framework-dependent-executables-fde"></a>Çerçeveye bağımlı yürütülebilir dosyalar (FDE)

.NET Core 2,2 ile başlayarak, uygulamanızı gerekli tüm üçüncü taraf bağımlılıklarıyla birlikte bir FDE olarak dağıtabilirsiniz. Uygulamanız, hedef sistemde yüklü olan .NET Core sürümünü kullanacaktır.

### <a name="why-deploy-a-framework-dependent-executable"></a>Çerçeveye bağlı bir çalıştırılabilir neden dağıtılsın?

Bir FDE dağıtmak bir dizi avantaja sahiptir:

- Dağıtım paketinizin boyutu küçüktür. Uygulamanızı ve bağımlılıklarını yalnızca .NET Core 'u değil, dağıtırsınız.

- Birden çok uygulama aynı .NET Core yüklemesini kullanır, bu da konak sistemlerindeki disk alanını ve bellek kullanımını azaltır.

- Uygulamanız, `dotnet` yardımcı programını doğrudan çağırmadan yayınlanan yürütülebilir dosya çağrılarak çalıştırılabilir.

Birkaç dezavantajın de vardır:

- Uygulamanız yalnızca, uygulamanızın hedeflediği .NET Core sürümü [veya daha sonraki bir sürüm](../versions/selection.md#framework-dependent-apps-roll-forward), ana bilgisayar sisteminde zaten yüklüyse çalıştırılabilir.

- .NET Core çalışma zamanı ve kitaplıklarının gelecek sürümlerde bilginiz olmadan değiştirilmesi mümkündür. Nadir durumlarda, bu durum uygulamanızın davranışını değiştirebilir.

- Uygulamanızı her bir hedef platform için yayımlamanız gerekir.

## <a name="step-by-step-examples"></a>Adım adım örnekler

CLı araçlarıyla .NET Core uygulamaları dağıtmanın adım adım örnekleri için bkz. [CLI araçları ile .NET Core uygulamaları dağıtma](deploy-with-cli.md). Visual Studio ile .NET Core uygulamaları dağıtmanın adım adım örnekleri için bkz. [Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md). 

## <a name="see-also"></a>Ayrıca bkz.

- [CLı araçları ile .NET Core uygulamaları dağıtma](deploy-with-cli.md)
- [Visual Studio ile .NET Core uygulamaları dağıtma](deploy-with-vs.md)
- [Paketler, Meta Paketler ve Çerçeveler](../packages.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
