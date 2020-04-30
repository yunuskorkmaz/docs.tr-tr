---
title: Hangi .NET Core sürümünün kullanılacağını seçin
description: .NET Core 'un programınızın çalışma zamanı sürümlerini otomatik olarak bulduğu ve seçtiği hakkında bilgi edinin. Ayrıca, bu makalede belirli bir sürümün nasıl zorlanacağı öğretilir.
author: thraka
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: 3c3d9b4ec5a68c88bdd0a45acfb49191f22abda4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595734"
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

SDK komutları ve `dotnet new` `dotnet run`içerir. .NET Core CLI her `dotnet` komut IÇIN bir SDK sürümü seçmeniz gerekir. Şu durumlarda bile varsayılan olarak makinede yüklü olan en son SDK 'yi kullanır:

- Proje .NET Core çalışma zamanının önceki bir sürümünü hedefliyor.
- .NET Core SDK en son sürümü bir önizleme sürümüdür.

Önceki .NET Core çalışma zamanı sürümlerini hedeflerken en son SDK özelliklerinden ve geliştirmelerinden yararlanabilirsiniz. .NET Core 'un birden fazla çalışma zamanı sürümünü, tüm projeler için aynı SDK araçlarını kullanarak farklı projelerde hedefleyebilirsiniz.

Nadir durumlarda, SDK 'nın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümü bir [ *Global. JSON* dosyasında](../tools/global-json.md)belirtirsiniz. "En son kullanım" ilkesi, en son yüklenen sürümden daha eski bir .NET Core SDK sürümünü belirtmek için yalnızca *Global. JSON* kullanacağınızı gösterir.

*Global. JSON* dosya hiyerarşisinde herhangi bir yere yerleştirilebilir. CLı, bulduğu ilk *Global. JSON* için proje dizininden yukarı doğru arama yapar. Verilen bir *Global. JSON* dosyası, dosya sistemindeki yerine hangi projelerin uygulanacağını kontrol edersiniz. .NET CLı, yolu geçerli çalışma dizininden yukarı doğru gezerek bir *Global. JSON* dosyası arar. Bulunan ilk *Global. JSON* dosyası kullanılan sürümü belirtiyor. Bu SDK sürümü yüklüyse, bu sürüm kullanılır. *Global. JSON* IÇINDE belirtilen SDK bulunamazsa, .net CLI uyumlu bir SDK seçmek için [eşleşen kuralları](../tools/global-json.md#matching-rules) kullanır veya Hiçbiri bulunmazsa başarısız olur.

Aşağıdaki örnek, *Global. JSON* sözdizimini göstermektedir:

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

SDK sürümü seçme işlemi şu şekilde yapılır:

1. `dotnet`Yinelenen bir *Global. JSON* dosyası arar ve yolu geçerli çalışma dizininden yukarı doğru geziyor.
1. `dotnet`bulunan ilk *Global. JSON* içinde belirtilen SDK 'yı kullanır.
1. `dotnet`*Global. JSON* bulunmazsa, en son yüklenen SDK 'yı kullanır.

*Genel. JSON*' daki makalenin [eşleştirme KURALLARı](../tools/global-json.md#matching-rules) bölümünde bir SDK sürümü seçme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef çerçeve takma adları derleme süresi API 'Lerini tanımlar

Projenizi bir **hedef çerçeve bilinen** adı 'nda (tfd) tanımlanan API 'lerle derleyin. [Hedef çerçevesini](../../standard/frameworks.md) proje dosyasında belirtirsiniz. Aşağıdaki örnekte `TargetFramework` gösterildiği gibi proje dosyanızdaki öğesini ayarlayın:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Projenizi birden çok TFMs 'ye karşı derleyebilirsiniz. Birden çok hedef çerçeveyi ayarlamak kitaplıklar için daha yaygındır, ancak uygulamalarla da gerçekleştirilebilir. Bir `TargetFrameworks` Özellik (çoğul `TargetFramework`) belirlersiniz. Hedef çerçeveler, aşağıdaki örnekte gösterildiği gibi noktalı virgülle ayrılmıştır:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Belirli bir SDK, birlikte geldiği çalışma zamanının hedef çerçevesine katıp sabit bir çerçeve kümesini destekler. Örneğin, .NET Core 3,0 SDK 'Sı, `netcoreapp3.0` hedef Framework 'ün uygulanması olan .net Core 3,0 çalışma zamanını içerir. .NET Core 3,0 `netcoreapp2.1`SDK, `netcoreapp2.2` `netcoreapp3.0`,,, ancak değil `netcoreapp3.1` (veya üzeri). İçin `netcoreapp3.1`derlemek üzere .net Core 3,1 SDK 'sını yüklersiniz.

.NET Standard hedef çerçeveler, SDK 'nın birlikte geldiği çalışma zamanının hedef çerçevesine de dönüştürülür. .NET Core 3,1 SDK 'Sı `netstandard2.1`. Daha fazla bilgi için bkz. [.NET Standard](../../standard/net-standard.md).

## <a name="framework-dependent-apps-roll-forward"></a>Çerçeveye bağımlı uygulamalar ileri alma

İle kaynağından [`dotnet run`](../tools/dotnet-run.md), [**çerçevesine bağlı bir dağıtımdan**](../deploying/index.md#publish-runtime-dependent) [`dotnet myapp.dll`](../tools/dotnet.md#description)veya ile [**çerçeveye bağlı bir yürütülebilirden**](../deploying/index.md#publish-runtime-dependent) `myapp.exe`uygulama çalıştırdığınızda, `dotnet` çalıştırılabilir dosya uygulamanın **ana bilgisayarı** olur.

Konak makinede yüklü en son düzeltme eki sürümünü seçer. Örneğin, proje dosyanızda belirttiyseniz `netcoreapp3.0` ve `3.0.4` en son .NET çalışma zamanı yüklüyse, `3.0.4` çalışma zamanı kullanılır.

Kabul edilebilir `3.0.*` bir sürüm bulunamazsa yeni `3.*` bir sürüm kullanılır. Örneğin, belirtilmişse `netcoreapp3.0` ve yalnızca `3.1.0` yüklüyse, uygulama `3.1.0` çalışma zamanını kullanarak çalışır. Bu davranış, "ikincil sürüm alma" olarak adlandırılır. Alt sürümler de göz önünde bulundurulmaz. Kabul edilebilir çalışma zamanı yüklü olmadığında uygulama çalıştırılmaz.

Birkaç kullanım örneği, 3,0 hedefliyorsanız davranışı gösterir:

- ✔️ 3,0 belirtildi. 3.0.5, en yüksek düzeltme eki sürümüdür. 3.0.5 kullanılır.
- ❌3,0 belirtildi. 3,0. * sürüm yüklendi. 2.1.1, en yüksek çalışma zamanının yüklü olduğunu. Bir hata iletisi görüntülenir.
- ✔️ 3,0 belirtildi. 3,0. * sürüm yüklendi. 3.1.0, en yüksek çalışma zamanı sürümüdür. 3.1.0 kullanılır.
- ❌2,0 belirtildi. 2. x sürümü yüklü değil. 3.0.0, en yüksek çalışma zamanının yüklü olduğunu. Bir hata iletisi görüntülenir.

İkincil sürüm al-ileri, son kullanıcıları etkileyebilecek bir yan etkiye sahiptir. Şu senaryoyu göz önünde bulundurun:

1. Uygulama, 3,0 'in gerekli olduğunu belirtir.
2. Çalıştırıldığında, 3,0. * sürümü yüklü değildir, ancak 3.1.0. Sürüm 3.1.0 kullanılacak.
3. Daha sonra, Kullanıcı 3.0.5 yükleyip uygulamayı yeniden çalıştırdığında 3.0.5 artık kullanılacaktır.

Özellikle ikili verileri serileştirme gibi senaryolar için 3.0.5 ve 3.1.0 farklı şekilde davranması olasıdır.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Kendi içindeki dağıtımlar seçili çalışma zamanını içerir

Bir uygulamayı [**kendi kendine dahil**](../deploying/index.md#publish-self-contained)edilen bir dağıtım olarak yayımlayabilirsiniz. Bu yaklaşım, uygulamanızla birlikte .NET Core çalışma zamanı ve kitaplıklarını paketler. Kendi içinde olan dağıtımlar çalışma zamanı ortamlarına bağımlılığı yoktur. Çalışma zamanı sürüm seçimi yayımlama zamanında gerçekleşir, çalışma zamanı değildir.

Yayımlama işlemi, belirtilen çalışma zamanı ailesinin en son düzeltme eki sürümünü seçer. Örneğin, .NET `dotnet publish` Core 3,0 çalışma zamanı ailesindeki en son düzeltme eki sürümledir, .NET Core 3.0.4 ' ı seçer. Hedef Framework (en son yüklenen güvenlik düzeltme ekleri dahil) uygulamayla birlikte paketlenir.

Bir uygulama için belirtilen minimum sürüm karşılanmazsa, bu bir hatadır. `dotnet publish`en son çalışma zamanı düzeltme eki sürümüne bağlar (belirli bir ana. ikincil sürüm ailesi içinde). `dotnet publish`, ' ın `dotnet run`geri iletme semantiğini desteklemez. Düzeltme ekleri ve bağımsız dağıtımlar hakkında daha fazla bilgi için .NET Core Uygulamaları Dağıtma konusundaki [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) başlıklı makaleye bakın.

Kendi içinde olan dağıtımlar belirli bir düzeltme eki sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi, proje dosyasında en düşük çalışma zamanı düzeltme eki sürümünü (daha yüksek veya daha düşük sürümlere) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>3.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Öğesi varsayılan sürüm ilkesini geçersiz kılar. Kendi içinde olan dağıtımlar için, `RuntimeFrameworkVersion` *tam* çalışma zamanı çerçevesi sürümünü belirtir. Çerçeveye bağımlı uygulamalar için gereken `RuntimeFrameworkVersion` *En düşük* çalışma zamanı çerçevesi sürümünü belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core indirin ve yükleyin](../install/index.md).
- [.NET Core çalışma zamanı ve SDK 'yı kaldırma](../install/remove-runtime-sdk-versions.md).
