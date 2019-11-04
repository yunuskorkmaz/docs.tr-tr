---
title: Hangi .NET Core sürümünün kullanılacağını seçin
description: .NET Core 'un programınızın çalışma zamanı sürümlerini otomatik olarak bulduğu ve seçtiği hakkında bilgi edinin. Ayrıca, bu makalede belirli bir sürümün nasıl zorlanacağı öğretilir.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.custom: seodec18
ms.openlocfilehash: 043b9b85633e81670783e7870f1be7726ab07e81
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454626"
---
# <a name="select-the-net-core-version-to-use"></a>Kullanılacak .NET Core sürümünü seçin

Bu makalede, .NET Core araçları, SDK ve sürümleri seçme çalışma zamanı tarafından kullanılan ilkeler açıklanmaktadır. Bu ilkeler, belirtilen sürümleri kullanarak çalışan uygulamalar arasında bir denge sağlar ve hem geliştirici hem de Son Kullanıcı makinelerini yükseltme kolaylığını etkinleştirir. Bu ilkeler aşağıdaki eylemleri gerçekleştirir:

- Güvenlik ve güvenilirlik güncelleştirmeleri dahil olmak üzere .NET Core 'un kolay ve verimli dağıtımı.
- Hedef çalışma zamanından bağımsız olarak en son araçları ve komutları kullanın.

Sürüm seçimi meydana gelir:

- SDK komutunu çalıştırdığınızda, [SDK en son yüklenen sürümü kullanır](#the-sdk-uses-the-latest-installed-version).
- Bir derleme oluşturduğunuzda, [hedef çerçeve takma adları derleme süresi API 'lerini tanımlar](#target-framework-monikers-define-build-time-apis).
- .NET Core uygulaması çalıştırdığınızda, [hedef çerçeveye bağımlı uygulamalar ileri sarma](#framework-dependent-apps-roll-forward).
- Kendi içinde olan bir uygulamayı yayımladığınızda, [kendi içinde kapsanan dağıtımlar seçili çalışma zamanını içerir](#self-contained-deployments-include-the-selected-runtime).

Bu belgenin geri kalanında bu dört senaryo incededir.

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK en son yüklü sürümü kullanıyor

SDK komutları `dotnet new` ve `dotnet run`içerir. .NET Core CLI her `dotnet` komutu için bir SDK sürümü seçmelidir. Şu durumlarda bile varsayılan olarak makinede yüklü olan en son SDK 'yi kullanır:

- Proje .NET Core çalışma zamanının önceki bir sürümünü hedefliyor.
- .NET Core SDK en son sürümü bir önizleme sürümüdür.

Önceki .NET Core çalışma zamanı sürümlerini hedeflerken en son SDK özelliklerinden ve geliştirmelerinden yararlanabilirsiniz. .NET Core 'un birden fazla çalışma zamanı sürümünü, tüm projeler için aynı SDK araçlarını kullanarak farklı projelerde hedefleyebilirsiniz.

Nadir durumlarda, SDK 'nın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümü bir [ *Global. JSON* dosyasında](../tools/global-json.md)belirtirsiniz. "En son kullanım" ilkesi, en son yüklenen sürümden daha eski bir .NET Core SDK sürümünü belirtmek için yalnızca *Global. JSON* kullanacağınızı gösterir.

*Global. JSON* dosya hiyerarşisinde herhangi bir yere yerleştirilebilir. CLı, bulduğu ilk *Global. JSON* için proje dizininden yukarı doğru arama yapar. Verilen bir *Global. JSON* dosyası, dosya sistemindeki yerine hangi projelerin uygulanacağını kontrol edersiniz. .NET CLı, yolu geçerli çalışma dizininden yukarı doğru gezerek bir *Global. JSON* dosyası arar. Bulunan ilk *Global. JSON* dosyası kullanılan sürümü belirtiyor. Bu SDK sürümü yüklüyse, bu sürüm kullanılır. *Global. JSON* IÇINDE belirtilen SDK bulunamazsa, .net CLI uyumlu bir SDK seçmek için [eşleşen kuralları](../tools/global-json.md#matching-rules) kullanır veya Hiçbiri bulunmazsa başarısız olur.

Aşağıdaki örnek, *Global. JSON* sözdizimini göstermektedir:

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

SDK sürümü seçme işlemi şu şekilde yapılır:

1. `dotnet`, geçerli çalışma dizininden yukarı doğru bir şekilde geri gidilerek bir *Global. JSON* dosyasını arar.
1. `dotnet`, bulunan ilk *Global. JSON* içinde belirtilen SDK 'yı kullanır.
1. `dotnet`, *Global. JSON* bulunmazsa, en son yüklenen SDK 'yı kullanır.

*Genel. JSON*' daki makalenin [eşleştirme KURALLARı](../tools/global-json.md#matching-rules) bölümünde bir SDK sürümü seçme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef çerçeve takma adları derleme süresi API 'Lerini tanımlar

Projenizi bir **hedef çerçeve bilinen** adı 'nda (tfd) tanımlanan API 'lerle derleyin. [Hedef çerçevesini](../../standard/frameworks.md) proje dosyasında belirtirsiniz. Proje dosyanızdaki `TargetFramework` öğesini aşağıdaki örnekte gösterildiği gibi ayarlayın:

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Projenizi birden çok TFMs 'ye karşı derleyebilirsiniz. Birden çok hedef çerçeveyi ayarlamak kitaplıklar için daha yaygındır, ancak uygulamalarla da gerçekleştirilebilir. Bir `TargetFrameworks` özelliği (`TargetFramework`çoğul) belirtirsiniz. Hedef çerçeveler, aşağıdaki örnekte gösterildiği gibi noktalı virgülle ayrılmıştır:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Belirli bir SDK, birlikte geldiği çalışma zamanının hedef çerçevesine katıp sabit bir çerçeve kümesini destekler. Örneğin, .NET Core 2,0 SDK, `netcoreapp2.0` hedef çerçevesinin bir uygulamasıdır .NET Core 2,0 çalışma zamanını içerir. .NET Core 2,0 SDK `netcoreapp1.0`, `netcoreapp1.1`ve `netcoreapp2.0` destekler, ancak `netcoreapp2.1` (veya üzeri) değil. `netcoreapp2.1`için derlemek üzere .NET Core 2,1 SDK 'sını yüklersiniz.

.NET Standard hedef çerçeveler, SDK 'nın birlikte geldiği çalışma zamanının hedef çerçevesine de dönüştürülür. .NET Core 2,0 SDK `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Çerçeveye bağımlı uygulamalar ileri alma

Bir uygulamayı [`dotnet run`](../tools/dotnet-run.md), [**çerçeveye bağlı bir dağıtımdan**](../deploying/index.md#framework-dependent-deployments-fdd) [`dotnet myapp.dll`](../tools/dotnet.md#description)veya `myapp.exe`olan [**çerçeveye bağlı bir yürütülebilirden**](../deploying/index.md#framework-dependent-executables-fde) çalıştırdığınızda, `dotnet` çalıştırılabilir dosyadır uygulama için.

Konak makinede yüklü en son düzeltme eki sürümünü seçer. Örneğin, proje dosyanızda `netcoreapp2.0` belirttiyseniz ve en son .NET çalışma zamanı yüklü `2.0.4`, `2.0.4` çalışma zamanı kullanılır.

Kabul edilebilir `2.0.*` sürümü bulunamazsa yeni bir `2.*` sürümü kullanılır. Örneğin, `netcoreapp2.0` belirttiyseniz ve yalnızca `2.1.0` yüklüyse, uygulama `2.1.0` çalışma zamanını kullanarak çalışır. Bu davranış, "ikincil sürüm alma" olarak adlandırılır. Alt sürümler de göz önünde bulundurulmaz. Kabul edilebilir çalışma zamanı yüklü olmadığında uygulama çalıştırılmaz.

Birkaç kullanım örneği, 2,0 hedefliyorsanız davranışı gösterir:

- 2,0 belirtildi. 2.0.5, en yüksek düzeltme eki sürümüdür. 2.0.5 kullanılır.
- 2,0 belirtildi. 2,0. * sürüm yüklendi. 1.1.1, en yüksek çalışma zamanının yüklü olduğunu. Bir hata iletisi görüntülenir.
- 2,0 belirtildi. 2,0. * sürüm yüklendi. 2.2.2, en yüksek 2. x çalışma zamanı sürümü yüklenir. 2.2.2 kullanılır.
- 2,0 belirtildi. 2\. x sürümü yüklü değil. 3.0.0 yüklendi. Bir hata iletisi görüntülenir.

İkincil sürüm al-ileri, son kullanıcıları etkileyebilecek bir yan etkiye sahiptir. Aşağıdaki senaryoyu göz önünde bulundurun:

1. Uygulama, 2,0 'in gerekli olduğunu belirtir.
2. Çalıştırıldığında, 2,0. * sürümü yüklü değildir, ancak 2.2.2. Sürüm 2.2.2 kullanılacak.
3. Daha sonra, Kullanıcı 2.0.5 yükleyip uygulamayı yeniden çalıştırdığında 2.0.5 artık kullanılacaktır.

Özellikle ikili verileri serileştirme gibi senaryolar için 2.0.5 ve 2.2.2 farklı şekilde davranması olasıdır.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Kendi içindeki dağıtımlar seçili çalışma zamanını içerir

Bir uygulamayı [**kendi kendine dahil**](../deploying/index.md#self-contained-deployments-scd)edilen bir dağıtım olarak yayımlayabilirsiniz. Bu yaklaşım, uygulamanızla birlikte .NET Core çalışma zamanı ve kitaplıklarını paketler. Kendi içinde olan dağıtımlar çalışma zamanı ortamlarına bağımlılığı yoktur. Çalışma zamanı sürüm seçimi yayımlama zamanında gerçekleşir, çalışma zamanı değildir.

Yayımlama işlemi, belirtilen çalışma zamanı ailesinin en son düzeltme eki sürümünü seçer. Örneğin, .NET Core 2,0 çalışma zamanı ailesindeki en son düzeltme eki sürümüdür `dotnet publish` .NET Core 2.0.4 ' yi seçmeyecektir. Hedef Framework (en son yüklenen güvenlik düzeltme ekleri dahil) uygulamayla birlikte paketlenir.

Bir uygulama için belirtilen minimum sürüm karşılanmazsa, bu bir hatadır. `dotnet publish`, en son çalışma zamanı düzeltme eki sürümüne bağlar (belirli bir ana. ikincil sürüm ailesi içinde). `dotnet publish`, `dotnet run`'ın geri alma semantiğini desteklemez. Düzeltme ekleri ve bağımsız dağıtımlar hakkında daha fazla bilgi için .NET Core Uygulamaları Dağıtma konusundaki [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) başlıklı makaleye bakın.

Kendi içinde olan dağıtımlar belirli bir düzeltme eki sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi, proje dosyasında en düşük çalışma zamanı düzeltme eki sürümünü (daha yüksek veya daha düşük sürümlere) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` öğesi varsayılan sürüm ilkesini geçersiz kılar. Kendi içinde olan dağıtımlar için `RuntimeFrameworkVersion`, *tam* çalışma zamanı Framework sürümünü belirtir. Çerçeveye bağımlı uygulamalar için `RuntimeFrameworkVersion`, gereken *En düşük* çalışma zamanı çerçevesi sürümünü belirtir.
