---
title: Hangi .NET Core sürümünün kullanılacağını seçin
description: .NET Core 'un programınızın çalışma zamanı sürümlerini otomatik olarak bulduğu ve seçtiği hakkında bilgi edinin. Ayrıca, bu makalede belirli bir sürümün nasıl zorlanacağı öğretilir.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.custom: seodec18
ms.openlocfilehash: db42ba4916aad739bd2c9d8b547f16022fce44bd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104942"
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

SDK komutları ve `dotnet new` `dotnet run`içerir. .NET Core CLI her `dotnet` komut için bir SDK sürümü seçmeniz gerekir. Şu durumlarda bile varsayılan olarak makinede yüklü olan en son SDK 'yi kullanır:

- Proje .NET Core çalışma zamanının önceki bir sürümünü hedefliyor.
- .NET Core SDK en son sürümü bir önizleme sürümüdür.

Önceki .NET Core çalışma zamanı sürümlerini hedeflerken en son SDK özelliklerinden ve geliştirmelerinden yararlanabilirsiniz. .NET Core 'un birden fazla çalışma zamanı sürümünü, tüm projeler için aynı SDK araçlarını kullanarak farklı projelerde hedefleyebilirsiniz.

Nadir durumlarda, SDK 'nın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümü bir [ *Global. JSON* dosyasında](../tools/global-json.md)belirtirsiniz. "En son kullanım" ilkesi, en son yüklenen sürümden daha eski bir .NET Core SDK sürümünü belirtmek için yalnızca *Global. JSON* kullanacağınızı gösterir.

*Global. JSON* dosya hiyerarşisinde herhangi bir yere yerleştirilebilir. CLı, bulduğu ilk *Global. JSON* için proje dizininden yukarı doğru arama yapar. Verilen bir *Global. JSON* dosyası, dosya sistemindeki yerine hangi projelerin uygulanacağını kontrol edersiniz. .NET CLı, yolu geçerli çalışma dizininden yukarı doğru gezerek bir *Global. JSON* dosyası arar. Bulunan ilk *Global. JSON* dosyası kullanılan sürümü belirtiyor. Bu sürüm yüklüyse, bu sürüm kullanılır. *Global. JSON* IÇINDE belirtilen SDK BULUNAMAZSA .net CLI, en son SDK 'nın yüklü olduğu bir sonraki sürüme kaydolur. Top-Forward, *Global. JSON* dosyası bulunamadığında varsayılan davranışla aynıdır.

Aşağıdaki örnek, *Global. JSON* sözdizimini göstermektedir:

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

SDK sürümü seçme işlemi şu şekilde yapılır:

1. `dotnet`Yinelenen bir *Global. JSON* dosyası arar ve yolu geçerli çalışma dizininden yukarı doğru geziyor.
1. `dotnet`bulunan ilk *Global. JSON* içinde belirtilen SDK 'yı kullanır.
1. `dotnet`*Global. JSON* bulunmazsa, en son yüklenen SDK 'yı kullanır.

*Genel. JSON*' daki makalenin [eşleştirme KURALLARı](../tools/global-json.md#matching-rules) bölümünde bir SDK sürümü seçme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef çerçeve takma adları derleme süresi API 'Lerini tanımlar

Projenizi bir **hedef çerçeve bilinen** adı 'nda (tfd) tanımlanan API 'lerle derleyin. [Hedef çerçevesini](../../standard/frameworks.md) proje dosyasında belirtirsiniz. Aşağıdaki örnekte gösterildiği gibi proje dosyanızdaki öğesiniayarlayın:`TargetFramework`

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Projenizi birden çok TFMs 'ye karşı derleyebilirsiniz. Birden çok hedef çerçeveyi ayarlamak kitaplıklar için daha yaygındır, ancak uygulamalarla da gerçekleştirilebilir. Bir `TargetFrameworks` Özellik ( `TargetFramework`çoğul) belirlersiniz. Hedef çerçeveler, aşağıdaki örnekte gösterildiği gibi noktalı virgülle ayrılmıştır:

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Belirli bir SDK, birlikte geldiği çalışma zamanının hedef çerçevesine katıp sabit bir çerçeve kümesini destekler. Örneğin, .NET Core 2,0 SDK 'sı, `netcoreapp2.0` hedef Framework 'ün uygulanması olan .NET Core 2,0 çalışma zamanını içerir. .Net `netcoreapp1.0`Core 2,0 SDK,, `netcoreapp1.1`ve `netcoreapp2.0` içermez `netcoreapp2.1` (veya üzeri). İçin `netcoreapp2.1`derlemek üzere .NET Core 2,1 SDK 'sını yüklersiniz.

.NET Standard hedef çerçeveler, SDK 'nın birlikte geldiği çalışma zamanının hedef çerçevesine de dönüştürülür. .NET Core 2,0 SDK 'Sı `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Çerçeveye bağımlı uygulamalar ileri alma

[`dotnet run`](../tools/dotnet-run.md)İle kaynak 'dan, [**çerçevesine**](../deploying/index.md#framework-dependent-deployments-fdd) [`dotnet myapp.dll`](../tools/dotnet.md#description)bağımlı bir dağıtımdan veya ile [**çerçevesine bağımlı**](../deploying/index.md#framework-dependent-executables-fde) bir yürütülebilirden `myapp.exe` `dotnet` uygulama çalıştırdığınızda, çalıştırılabilir dosyadıruygulama için.

Konak makinede yüklü en son düzeltme eki sürümünü seçer. Örneğin, proje dosyanızda belirttiyseniz `netcoreapp2.0` ve `2.0.4` en son `2.0.4` .NET çalışma zamanı yüklüyse, çalışma zamanı kullanılır.

Kabul edilebilir `2.0.*` bir sürüm bulunamazsa yeni `2.*` bir sürüm kullanılır. Örneğin, belirtilmişse `netcoreapp2.0` ve yalnızca `2.1.0` yüklüyse, uygulama `2.1.0` çalışma zamanını kullanarak çalışır. Bu davranış, "ikincil sürüm alma" olarak adlandırılır. Alt sürümler de göz önünde bulundurulmaz. Kabul edilebilir çalışma zamanı yüklü olmadığında uygulama çalıştırılmaz.

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

Yayımlama işlemi, belirtilen çalışma zamanı ailesinin en son düzeltme eki sürümünü seçer. Örneğin, .net `dotnet publish` Core 2,0 çalışma zamanı ailesindeki en son düzeltme eki sürümledir, .NET Core 2.0.4 ' ı seçer. Hedef Framework (en son yüklenen güvenlik düzeltme ekleri dahil) uygulamayla birlikte paketlenir.

Bir uygulama için belirtilen minimum sürüm karşılanmazsa, bu bir hatadır. `dotnet publish`en son çalışma zamanı düzeltme eki sürümüne bağlar (belirli bir ana. ikincil sürüm ailesi içinde). `dotnet publish`, ' ın `dotnet run`geri iletme semantiğini desteklemez. Düzeltme ekleri ve bağımsız dağıtımlar hakkında daha fazla bilgi için .NET Core Uygulamaları Dağıtma konusundaki [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) başlıklı makaleye bakın.

Kendi içinde olan dağıtımlar belirli bir düzeltme eki sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi, proje dosyasında en düşük çalışma zamanı düzeltme eki sürümünü (daha yüksek veya daha düşük sürümlere) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` Öğesi varsayılan sürüm ilkesini geçersiz kılar. Kendi içinde olan dağıtımlar `RuntimeFrameworkVersion` için, *tam* çalışma zamanı çerçevesi sürümünü belirtir. Çerçeveye bağımlı uygulamalar `RuntimeFrameworkVersion` için gereken *En düşük* çalışma zamanı çerçevesi sürümünü belirtir.
