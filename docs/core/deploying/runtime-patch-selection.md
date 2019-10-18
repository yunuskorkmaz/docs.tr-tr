---
title: .NET Core 'un kendi içindeki uygulama dağıtımları için çalışma zamanı ileri iletme.
description: Kendi içindeki dağıtımlar için dotnet publish değişiklikler hakkında bilgi edinin.
author: KathleenDollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: 6a0cdfb34973822c2f40cdb37d4038d3b7ad8e2a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522095"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Kendi içinde dağıtım çalışma zamanını ileri sarma

.NET Core, [kendi içinde bulunan uygulama dağıtımları](index.md) hem .NET Core kitaplıklarını hem de .NET Core çalışma zamanını içerir. .NET Core 2,1 SDK (sürüm 2.1.300) ' den başlayarak, otomatik olarak kapsanan bir uygulama dağıtımı [makinenizde en yüksek düzeltme eki çalışma zamanını yayımlar](https://github.com/dotnet/designs/pull/36). Varsayılan olarak, kendinden bağımsız bir dağıtım için [`dotnet publish`](../tools/dotnet-publish.md) YAYıMLAMA makinesinde SDK 'nın bir parçası olarak yüklenen en son sürümü seçer. Bu, dağıtılan uygulamanızın `publish` sırasında kullanılabilir güvenlik düzeltmeleri (ve diğer düzeltmeler) ile çalışmasını sağlar. Uygulamanın yeni bir düzeltme eki edinmek için yeniden yayımlanması gerekir. Kendi içinde bulunan uygulamalar, `dotnet publish` komutunda `-r <RID>` belirterek veya proje dosyasında (csproj/vbproj) veya komut satırında [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtilerek oluşturulur.

## <a name="patch-version-roll-forward-overview"></a>Düzeltme Eki Sürümü ileri bakış

[`restore`](../tools/dotnet-restore.md), [`build`](../tools/dotnet-build.md) ve [`publish`](../tools/dotnet-publish.md) ayrı olarak çalışabilen `dotnet` komutlardır. Çalışma zamanı seçeneği, `publish` veya `build` değil `restore` işlemin bir parçasıdır. @No__t_0 çağırırsanız, en son düzeltme eki sürümü seçilir. @No__t_1 bağımsız değişkeniyle `publish` çağırırsanız, önceki bir `restore` yeni uygulama yayımlama ilkesiyle yürütülmemiş olabileceği için, istenen düzeltme eki sürümünü de alamıyoruz. Bu durumda, aşağıdakine benzer bir metin içeren bir yapı hatası oluşturulur:

  "Proje Microsoft. NETCore. App sürüm 2.0.0 kullanılarak geri yüklendi, ancak geçerli ayarlarla sürüm 2.0.6 kullanılacak. Bu sorunu çözmek için, geri yükleme ve derleme ya da yayımlama gibi sonraki işlemler için aynı ayarların kullanıldığından emin olun. Genellikle bu sorun, Runtimeıdentifier özelliği Build veya Publish sırasında ayarlandıysa, geri yükleme sırasında olmasa da oluşabilir. "

> [!NOTE]
> `restore` ve `build`, `publish` gibi başka bir komutun parçası olarak örtük olarak çalıştırılabilir. Başka bir komutun parçası olarak örtük olarak çalıştırıldığında, doğru yapıtların üretilmesi için ek bağlamla birlikte sağlanır. Bir çalışma zamanı ile `publish` (örneğin, `dotnet publish -r linux-x64`), örtük `restore` Linux-x64 çalışma zamanının paketlerini geri yükler. Açıkça `restore` çağırırsanız, bu bağlamı içermediğinden çalışma zamanı paketlerini varsayılan olarak geri yüklemez.

## <a name="how-to-avoid-restore-during-publish"></a>Yayımlama sırasında geri yükleme nasıl önlenir

@No__t_1 işleminin bir parçası olarak `restore` çalıştırmak, senaryonuz için istenmeyen bir işlem olabilir. @No__t_1 sırasında, kendi içinde bulunan uygulamalar oluştururken `restore` önlemek için şunları yapın:

- @No__t_0 özelliğini, yayımlanacak tüm [RID](../rid-catalog.md) 'lerin noktalı virgülle ayrılmış bir listesi olarak ayarlayın.
- @No__t_0 özelliğini `true` olarak ayarlayın.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>dotnet publish seçenekleriyle geri yükleme olmayan bağımsız değişken

Aynı proje dosyası ile hem kendi içinde hem de [çerçeveye bağımlı uygulamalar](index.md) oluşturmak istiyorsanız ve `dotnet publish` `--no-restore` bağımsız değişkenini kullanmak istiyorsanız aşağıdakilerden birini seçin:

1. Çerçeveye bağımlı davranışı tercih edin. Uygulama çerçeveye bağımlıysa, bu varsayılan davranıştır. Uygulama kendi kendine dahil ise ve düzeltme eki yüklenmemiş 2.1.0 yerel çalışma zamanını kullanıyorsa, `TargetLatestRuntimePatch` proje dosyasında `false` olarak ayarlayın.

2. Kendi kendine içerilen davranışı tercih edin. Uygulama kendinden içeriyorsa, varsayılan davranıştır. Uygulama çerçeveye bağımlıdır ve en son düzeltme eki yüklenmesini gerektiriyorsa, `TargetLatestRuntimePatch` proje dosyasında `true` olarak ayarlayın.

3. Proje dosyasındaki belirli bir düzeltme eki sürümüne `RuntimeFrameworkVersion` ayarlayarak çalışma zamanı çerçevesi sürümünün açık denetimini alın.
