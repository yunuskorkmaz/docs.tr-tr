---
title: Hangi .NET Core sürümünün kullanılacağını seçin
description: .NET Core'un programınız için çalışma zamanı sürümlerini otomatik olarak nasıl bulduğunu ve seçtiğini öğrenin. Ayrıca, bu makalede nasıl belirli bir sürümünü zorlamak için öğretir.
author: thraka
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: 26aecdf2bf3ebd033e80eec26159eb9fa3cd54dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345166"
---
# <a name="select-the-net-core-version-to-use"></a>Kullanmak için .NET Core sürümünü seçin

Bu makalede, .NET Core araçları, SDK ve sürümleri seçmek için çalışma zamanı tarafından kullanılan ilkeler açıklanmaktadır. Bu ilkeler, belirtilen sürümleri kullanarak uygulamaları çalıştırma ve hem geliştirici hem de son kullanıcı makinelerini yükseltme kolaylığı sağlamak arasında bir denge sağlar. Bu ilkeler aşağıdaki eylemleri gerçekleştirir:

- Güvenlik ve güvenilirlik güncelleştirmeleri de dahil olmak üzere .NET Core'un kolay ve verimli dağıtımı.
- Hedef çalışma zamanından bağımsız olarak en son araçları ve komutları kullanın.

Sürüm seçimi oluşur:

- Bir SDK komutu çalıştırdığınızda, [SDK en son yüklenen sürümü kullanır.](#the-sdk-uses-the-latest-installed-version)
- Bir derleme oluşturduğunuzda, [hedef çerçeve monikers yapı süresi API'leri tanımlar.](#target-framework-monikers-define-build-time-apis)
- Bir .NET Core uygulaması çalıştırdığınızda, [hedef çerçeveye bağımlı uygulamalar ileri ye doğru yuvarlanıyor.](#framework-dependent-apps-roll-forward)
- Bağımsız bir uygulama yayımladığınızda, [bağımsız dağıtımlar seçili çalışma süresini içerir.](#self-contained-deployments-include-the-selected-runtime)

Bu belgenin geri kalanı bu dört senaryoyu inceler.

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK en son yüklenen sürümü kullanır

SDK komutları `dotnet new` `dotnet run`içerir ve . .NET Core CLI her `dotnet` komut için bir SDK sürümü seçmelidir. Aşağıdakiler olsa bile, varsayılan olarak makineye yüklenen en son SDK'yı kullanır:

- Proje,.NET Core çalışma zamanının önceki bir sürümünü hedefler.
- .NET Core SDK'nın en son sürümü bir önizleme sürümüdür.

Önceki .NET Core çalışma zamanı sürümlerini hedefalırken en son SDK özelliklerinden ve geliştirmelerinden yararlanabilirsiniz. Tüm projeler için aynı SDK araçlarını kullanarak .NET Core'un birden çok çalışma zamanı sürümlerini farklı projelerde hedefleyebilirsiniz.

Nadir durumlarda, SDK'nın önceki bir sürümünü kullanmanız gerekebilir. Bu sürümü [ *global.json* dosyasında](../tools/global-json.md)belirtirsiniz. "En son kullan" ilkesi, *global.json'ı* yalnızca .NET Core SDK sürümünü en son yüklenen sürümden daha erken belirtmek için kullandığınız anlamına gelir.

*global.json* dosya hiyerarşisinde herhangi bir yere yerleştirilebilir. CLI, bulduğu ilk *global.json* için proje dizininden yukarı doğru arama lar arar. Belirli bir *global.json'Un* dosya sistemindeki yeri ile hangi projelere uygulanabilen bir proje olduğunu siz denetlersiniz. .NET CLI, bir *global.json* dosyasını arar ve yolu geçerli çalışma dizininden yukarı doğru geziner. Bulunan ilk *global.json* dosyası, kullanılan sürümü belirtir. Bu SDK sürümü yüklenmişse, bu sürüm kullanılır. *global.json'da* belirtilen SDK bulunamazsa, .NET CLI uyumlu bir SDK seçmek için [eşleşen kurallar](../tools/global-json.md#matching-rules) kullanır veya yoksa başarısız olur.

Aşağıdaki *örnekglobal.json* sözdizimini gösterir:

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

SDK sürümünü seçme işlemi:

1. `dotnet`*global.json* dosyası için arama lar, geçerli çalışma dizininden yukarı doğru yol üzerinde yinelemeli olarak ters gezinme.
1. `dotnet`bulunan ilk *global.json* belirtilen SDK kullanır.
1. `dotnet`*global.json* bulunamazsa en son yüklenen SDK'yı kullanır.

*Global.json*hakkındaki makalenin [Eşleşen kurallar](../tools/global-json.md#matching-rules) bölümünde bir SDK sürümü seçme hakkında daha fazla bilgi edinebilirsiniz.

## <a name="target-framework-monikers-define-build-time-apis"></a>Hedef Çerçeve Monikers yapı süresi API'leri tanımlamak

Projenizi **Hedef Çerçeve Takma Adı** 'nda (TFM) tanımlanan API'ler'e karşı oluşturursunuz. Proje dosyasındaki [hedef çerçeveyi](../../standard/frameworks.md) belirtirsiniz. Proje `TargetFramework` dosyanızdaki öğeyi aşağıdaki örnekte gösterildiği şekilde ayarlayın:

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Projenizi birden çok TFM'ye karşı oluşturabilirsiniz. Birden çok hedef çerçeveleri ayarlama kitaplıklar için daha yaygındır, ancak uygulamalarla da yapılabilir. Bir `TargetFrameworks` özellik (çoğul) belirtirsiniz. `TargetFramework` Hedef çerçeveler aşağıdaki örnekte gösterildiği gibi yarı kolon-delimited vardır:

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

Belirli bir SDK, birlikte sevk edilen çalışma zamanının hedef çerçevesine kapaklı sabit bir çerçeve kümesini destekler. Örneğin, .NET Core 3.0 SDK `netcoreapp3.0` hedef çerçevenin bir uygulamasıdır .NET Core 3.0 çalışma süresini içerir. .NET Core 3.0 SDK `netcoreapp2.1`destekler , , `netcoreapp2.2` `netcoreapp3.0`, ama değil `netcoreapp3.1` (veya daha yüksek). .NET Core 3.1 SDK'yı `netcoreapp3.1`kurmak için yüklersiniz.

.NET Standart hedef çerçeveleri de SDK gemilerinin çalışma zamanının hedef çerçevesine kapaklanır. .NET Core 3.1 SDK `netstandard2.1`ile kapatılır. Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md)' a bakın.

## <a name="framework-dependent-apps-roll-forward"></a>Çerçeveye bağımlı uygulamalar ileri sarma

Bir [`dotnet run`](../tools/dotnet-run.md)uygulamayı kaynaktan , [**framework'e bağımlı**](../deploying/index.md#publish-runtime-dependent) bir [`dotnet myapp.dll`](../tools/dotnet.md#description)dağıtımdan veya framework'e `myapp.exe`bağımlı `dotnet` bir [**yürütülebilir**](../deploying/index.md#publish-runtime-dependent) ile çalıştırdığınızda çalıştırılabilir uygulamanın **ana bilgisayarı** dır.

Ana bilgisayar, makineye yüklenen en son yama sürümünü seçer. Örneğin, proje dosyanızda belirttiyseniz `netcoreapp3.0` ve `3.0.4` en son .NET çalışma zamanı `3.0.4` yüklüyse, çalışma zamanı kullanılır.

Kabul edilebilir `3.0.*` bir sürüm bulunamazsa, yeni `3.*` bir sürüm kullanılır. Örneğin, belirttiyseniz `netcoreapp3.0` ve `3.1.0` yalnızca yüklüyse, uygulama `3.1.0` çalışma süresini kullanarak çalışır. Bu davranışa "küçük sürüm roll-forward" adı verilir. Alt sürümler de dikkate alınmaz. Kabul edilebilir bir çalışma zamanı yüklenmiyorsa, uygulama çalışmaz.

3.0'ı hedefliyorsanız, davranışı gösteren birkaç kullanım örneği:

- ✔️ 3.0 belirtilir. 3.0.5 en yüksek yama sürümü yüklenir. 3.0.5 kullanılır.
- ❌3.0 belirtilir. 3.0.* sürümü yoktur. 2.1.1 en yüksek çalışma süresi yüklenir. Bir hata iletisi görüntülenir.
- ✔️ 3.0 belirtilir. 3.0.* sürümü yoktur. 3.1.0, yüklenen en yüksek çalışma zamanı sürümüdür. 3.1.0 kullanılır.
- ❌2.0 belirtilir. 2.x sürümü yok. 3.0.0 en yüksek çalışma süresi yüklenir. Bir hata iletisi görüntülenir.

Küçük sürüm roll-forward son kullanıcıları etkileyebilecek bir yan etkisi vardır. Şu senaryoyu göz önünde bulundurun:

1. Uygulama 3.0 gerekli olduğunu belirtir.
2. Çalıştırıldığında, sürüm 3.0.* yüklenmez, ancak 3.1.0'dır. Sürüm 3.1.0 kullanılacaktır.
3. Daha sonra, kullanıcı 3.0.5 yükler ve uygulamayı yeniden çalıştırın, 3.0.5 şimdi kullanılacaktır.

3.0.5 ve 3.1.0'ın, özellikle ikili verileri serihale etme gibi senaryolarda farklı davranması mümkündür.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Bağımsız dağıtımlar, seçili çalışma süresini içerir

Bir uygulamayı bağımsız bir dağıtım olarak [**yayımlayabilirsiniz.**](../deploying/index.md#publish-self-contained) Bu yaklaşım, .NET Core çalışma zamanını ve kitaplıklarını uygulamanızla bir araya alır. Bağımsız dağıtımların çalışma zamanı ortamlarına bağımlılığı yoktur. Çalışma zamanı sürüm seçimi, çalışma zamanında değil, yayımlama zamanında gerçekleşir.

Yayımlama işlemi, verilen çalışma zamanı ailesinin en son yama sürümünü seçer. Örneğin, `dotnet publish` .NET Core 3.0 çalışma zamanı ailesindeki en son yama sürümüyse .NET Core 3.0.4'u seçer. Hedef çerçeve (en son yüklenen güvenlik yamaları dahil) uygulama ile birlikte paketlenir.

Bir uygulama için belirtilen minimum sürüm karşılanmamışsa bu bir hatadır. `dotnet publish`en son çalışma zamanı yama sürümüne bağlanır (belirli bir major.minor sürüm ailesi içinde). `dotnet publish`roll-forward semantikini `dotnet run`desteklemez. Yamalar ve bağımsız dağıtımlar hakkında daha fazla bilgi için .NET Core uygulamalarını dağıtan [çalışma zamanı düzeltme eki seçimi](../deploying/runtime-patch-selection.md) yle ilgili makaleye bakın.

Bağımsız dağıtımlar belirli bir yama sürümü gerektirebilir. Aşağıdaki örnekte gösterildiği gibi proje dosyasındaki minimum çalışma zamanı düzeltme ekini (daha yüksek veya daha düşük sürümlere) geçersiz kılabilirsiniz:

``` xml
<RuntimeFrameworkVersion>3.0.4</RuntimeFrameworkVersion>
```

Öğe `RuntimeFrameworkVersion` varsayılan sürüm ilkesini geçersiz kılar. Bağımsız dağıtımlar için, `RuntimeFrameworkVersion` *tam* çalışma zamanı çerçeve sürümünü belirtir. Çerçeveye bağımlı uygulamalar için, gerekli `RuntimeFrameworkVersion` *en az* çalışma zamanı çerçeve sürümünü belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core'u indirin ve kurun.](../install/index.md)
- [Nasıl .NET Çekirdek Çalışma Süresi ve SDK kaldırmak için.](remove-runtime-sdk-versions.md)
