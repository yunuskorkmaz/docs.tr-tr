---
title: .NET core sürüm seçimi
description: .NET Core nasıl bulur ve programınızın çalışma zamanı sürümleri seçer öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 21697aa773abfbd88288d47323402a48c51d69ae
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140170"
---
# <a name="net-core-version-selection"></a>.NET core sürüm seçimi

[!INCLUDE [topic-appliesto-net-core-2plus](../../../includes/topic-appliesto-net-core-2plus.md)]

Bu makalede, .NET Core araçları, SDK ve çalışma zamanı sürümleri seçmek için kullanılan ilkeleri açıklanır. Bu ilkeler çalışan uygulamalar belirtilen sürümlerini kullanan ve etkinleştirme kolaylaştırır hem geliştirme hem de son kullanıcı makineleri yükseltme arasında bir denge sağlar. Bu ilkeler, aşağıdaki eylemleri gerçekleştirin:

- .NET Core, güvenlik ve güvenilirlik güncelleştirmeleri dahil olmak üzere kolay ve verimli dağıtımı.
- En son araçları ve hedef çalışma zamanı bağımsız komutları kullanın.

Sürüm seçimi oluşur:

- Bir SDK komutu çalıştırdığınızda [en son yüklenen sürüm sdk kullanan](#the-sdk-uses-the-latest-installed-version).
- Bir derleme oluşturduğunuzda [hedef çerçeve bilinen adlar tanımlama derleme zamanı API'leri](#target-framework-monikers-define-build-time-apis).
- Bir .NET Core uygulamasını çalıştırdığınızda [hedef framework bağımlı uygulamaları alma İleri](#framework-dependent-apps-roll-forward).
- Kendi içinde bir uygulama yayımladığınızda [müstakil dağıtımları içerecek seçili olan çalışma zamanını](#self-contained-deployments-include-the-selected-runtime).

Bu belgenin geri kalan bu dört senaryo inceler.

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK'sı en son yüklenen sürüm kullanır.

SDK'sı seçeneğindeki `dotnet new`,, veya `dotnet run`. `dotnet` CLI gereken herhangi bir komutun bir SDK sürümü seçin. .NET Core CLI makinede varsayılan olarak yüklü en son SDK'sını kullanır. Yüklendiğinde, .NET Core çalışma zamanı 2.0 hedefleriyle çalıştığınız proje olsa bile, .NET Core SDK'sı v2.1.301 kullanırsınız. En son Önizleme sürümlerini kullanacaktır yanı sıra yayımlanan sürümleri. Önceki .NET Core çalışma zamanı sürümleri hedefleyen sırasında en son SDK'sı özellikleri ve geliştirmeleri avantajlarından alabilir. Tüm projelerde aynı SDK araçları kullanarak .NET Core farklı projelerde birden fazla çalışma zamanı sürümünü hedefleyebilirsiniz.

Nadir durumlarda, SDK'ın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümde, belirttiğiniz bir [ *global.json* dosya](../tools/global-json.md). "En günceli kullan" ilke yalnızca kullanmak anlamına gelir *global.json* en son yüklenen sürüm'den önceki bir .NET Core SDK sürümünü belirtmek için.

*Global.JSON* dosya hiyerarşideki herhangi bir yerde yerleştirilebilir. CLI'yı arar yukarı ilk proje dizininden *global.json* bulduğu. Hangi projelerini denetleyecek bir verilen *global.json* tarafından onun yerine dosya sistemindeki uygulanır. .NET CLI arar bir *global.json* çalıştırmalarınızı geçerli çalışma dizini yolundan yukarı gezinme dosya. İlk *global.json* dosya bulundu kullanılan sürümünü belirtir. Bu sürüm yüklü değilse, bu sürümü kullanılır. SDK'sı belirtilmişse *global.json* bulunamadı, .NET CLI yüklü en son SDK İleri yapar. Varsayılan davranış, hiçbir aynı sarma *global.json* dosya bulundu.

Aşağıdaki örnekte gösterildiği *global.json* söz dizimi:

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

SDK sürümü seçmek için işlemdir:

1. `dotnet` arar bir *global.json* çalıştırmalarınızı ters-geçerli çalışma dizini yolundan yukarı gezinme dosya.
1. `dotnet` ilk belirtilen SDK'sı kullanır *global.json* bulunamadı.
1. `dotnet` kullanan en son yüklü SDK yoksa *global.json* bulunur.

Bir SDK sürümünde seçme hakkında daha fazla bilgi [kurallarına](../tools/global-json.md#matching-rules) makale bölümünde *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef Çerçeve bilinen adlar derleme zamanı API'leri tanımlama

Tanımlanan API'leri karşı projenizi bir **hedef çerçeve adı** (TFM). Belirttiğiniz [hedef Framework'ü](../../standard/frameworks.md) proje dosyasındaki. Ayarlama `TargetFramework` öğesi aşağıdaki örnekte gösterildiği gibi proje dosyasında:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Birden çok Tfm'ler karşı projenizi. Birden çok hedef çerçeve ayarını kitaplıkları için daha yaygın bir durumdur, ancak uygulamalarla de yapılabilir. Belirttiğiniz bir `TargetFrameworks` özelliği (çoğul, `TargetFramework`). Hedef Çerçeve noktalı virgül-aşağıdaki örnekte gösterildiği gibi sınırlandırılmıştır:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Belirli bir SDK'sı ile birlikte gelen çalışma zamanı hedef çerçeve tavan çerçeveleri, sabit bir kümesini destekler. Örneğin, .NET Core 2.0 SDK'sını uygulamasıdır .NET Core 2.0 çalışma zamanı içerir, `netcoreapp2.0` hedef çerçeve. .NET Core 2.0 SDK'sını destekleyen `netcoreapp1.0`, `netcoreapp1.1`, ve `netcoreapp2.0` ama `netcoreapp2.1` (veya üzeri). Oluşturmak için .NET Core 2.1 SDK yükleme `netcoreapp2.1`.

.NET standard hedef çerçeve hedef çerçeve SDK'sı ile birlikte gelen çalışma zamanı ayrıca kapsanır. .NET Core 2.0 SDK'sı için tavan `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Framework bağımlı uygulamaları ileri sarma

Bir uygulama ile kaynağından çalıştırma [ `dotnet run` ](../tools/dotnet-run.md). `dotnet run` hem oluşturur ve bir uygulama çalıştırır. `dotnet` Yürütülebilir olduğundan **konak** geliştirme ortamlarında uygulama için.

Ana makinede yüklü en son düzeltme eki sürümü seçer. Örneğin, belirttiğiniz `netcoreapp2.0` proje dosyanızda ve `2.0.4` yüklüyse, en son .NET çalışma zamanı `2.0.4` çalışma zamanı kullanılır.

Hayır edilebilirse `2.0.*` sürümü bulundu, yeni bir `2.*` sürümü kullanılır. Örneğin, belirttiğiniz `netcoreapp2.0` ve yalnızca `2.1.0` kullanarak uygulama çalışırken, yüklü `2.1.0` çalışma zamanı. Bu davranışı "alt sürüm sarma." adlandırılır Ayrıca daha düşük sürümler kabul olmaz. Kabul edilebilir hiçbir çalışma zamanı yüklendiğinde, uygulama çalışmaz.

Birkaç kullanım örnekleri davranış gösterir:

- 2.0.4 gereklidir. 2.0.5 yüksek düzeltme eki sürümü yüklü olduğu. 2.0.5 kullanılan.
- 2.0.4 gereklidir. Hayır 2.0. * sürümleri yüklenir. 1.1.1 yüklü olan en yüksek çalışma zamanı ' dir. Bir hata iletisi görüntülenir.
- 2.0.4 gereklidir. 2.0.0 yüklü en yüksek sürüm var. Bir hata iletisi görüntülenir.
- 2.0.4 gereklidir. Hayır 2.0. * sürümleri yüklenir. 2.2.2 yüksek 2.x çalışma zamanı sürümü var. 2.2.2 kullanılan.
- 2.0.4 gereklidir. Hiçbir 2.x sürümleri yüklenir. 3.0.0 (şu anda kullanılabilir bir sürümü değil) yüklenir. Bir hata iletisi görüntülenir.

Alt sürüm sarma bir yan son kullanıcıların etkileyebilecek etkisi vardır. Aşağıdaki senaryoyu göz önünde bulundurun:

- 2.0.4 gereklidir. Hayır 2.0. * sürümleri yüklenir. 2.2.2 yüklü. 2.2.2 kullanılan.
- 2.0.5 daha sonra yüklenir. sonraki uygulaması açılır, değil 2.2.2 2.0.5 kullanılır. En son düzeltme eki gerekli ikincil sürümü üzerinde daha yüksek bir ikincil sürüm tercih edilir.
- 2.0.5 ve 2.2.2 farklı şekilde, özellikle ikili verileri seri hale getirme gibi senaryolar için davrandığını mümkündür.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Seçili olan çalışma zamanını müstakil dağıtımları içerecek

Bir uygulama olarak yayımlayabilirsiniz bir [ **müstakil dağıtım**](../deploying/index.md#self-contained-deployments-scd). Bu yaklaşım, .NET Core çalışma zamanı ve kitaplıkları uygulamanız ile oluşturur. Bağımsız dağıtımlar çalışma zamanı ortamlarını üzerinde bir bağımlılık yok. Çalışma zamanı sürüm seçimi, çalışma zamanı değil, yayımlanma tarihinde gerçekleşir.

Yayımlama işlemi, belirtilen çalışma zamanı ailesi en son düzeltme eki sürümü seçer. Örneğin, `dotnet publish` en son düzeltme eki sürümü .NET Core 2.0 çalışma zamanı ailesindeki ise .NET Core 2.0.4 seçer. Hedef Framework'ü (en son yüklenen güvenlik düzeltme ekleri dahil), uygulama ile paketlenmiştir.

Bir uygulama için belirtilen en düşük sürüm memnun değil, bir hata var. `dotnet publish` en son çalışma zamanı düzeltme eki sürümü (içinde verilen AnaSürüm.altsürüm sürüm ailesi) bağlar. `dotnet publish` sarma semantiği desteklemiyor `dotnet run`. Düzeltme ekleri ve müstakil dağıtımları hakkında daha fazla bilgi için makaleye bakın [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) .NET Core uygulamaları dağıtmak.

Bağımsız dağıtımlar, belirli bir düzeltme eki sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi proje dosyasında en az bir çalışma zamanı düzeltme eki sürümü (daha yüksek veya düşük sürümler için) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Öğesini varsayılan sürüm ilkesini geçersiz kılar. Bağımsız dağıtımlar için `RuntimeFrameworkVersion` belirtir *tam* çalışma zamanı framework sürümü. Framework bağımlı uygulamalar için `RuntimeFrameworkVersion` belirtir *minimum* gerekli çalışma zamanı framework sürümü.
