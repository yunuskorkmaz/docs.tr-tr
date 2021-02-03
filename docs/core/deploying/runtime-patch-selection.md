---
title: .NET Core 'un kendi içindeki uygulama dağıtımları için çalışma zamanı ileri iletme.
description: Kendi içindeki dağıtımlar için dotnet publish değişiklikler hakkında bilgi edinin.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 6bc578c63b28f51f1dd98e3e7e56fbe2c7a3e7cf
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505914"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Kendi içinde dağıtım çalışma zamanını ileri sarma

.NET Core, [kendi içinde bulunan uygulama dağıtımları](index.md) hem .NET Core kitaplıklarını hem de .NET Core çalışma zamanını içerir. .NET Core 2,1 SDK (sürüm 2.1.300) ' den başlayarak, otomatik olarak kapsanan bir uygulama dağıtımı [makinenizde en yüksek düzeltme eki çalışma zamanını yayımlar](https://github.com/dotnet/designs/blob/main/accepted/2018/self-contained-roll-forward.md). Varsayılan olarak, [`dotnet publish`](../tools/dotnet-publish.md) otomatik olarak kapsanan bir dağıtım için yayımlama MAKINESINDE SDK 'nın bir parçası olarak yüklenen en son sürümü seçer. Bu, dağıtılan uygulamanızın sırasında kullanılabilir olan güvenlik düzeltmeleri (ve diğer düzeltmeler) ile çalışmasını sağlar `publish` . Yeni bir yama elde etmek için uygulamanın yeniden yayımlanması gerekir. Kendi içinde bulunan uygulamalar `-r <RID>` , `dotnet publish` komutu belirtilerek veya proje dosyasında (csproj/vbproj) veya komut satırında [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtilerek oluşturulur.

## <a name="patch-version-roll-forward-overview"></a>Düzeltme Eki Sürümü ileri bakış

[`restore`](../tools/dotnet-restore.md), [`build`](../tools/dotnet-build.md) ve [`publish`](../tools/dotnet-publish.md) `dotnet` ayrı olarak çalışabilen komutlardır. Çalışma zamanı seçeneği `restore` , veya değil, işlemin bir parçasıdır `publish` `build` . `publish`Öğesini çağırdığınızda, en son düzeltme eki sürümü seçilir. `publish` `--no-restore` Bağımsız değişkenle birlikte çağırırsanız, önceki `restore` Yeni uygulama yayımlama ilkesiyle birlikte yürütülmemiş olabileceği için, istenen düzeltme eki sürümünü de alamıyoruz. Bu durumda, aşağıdakine benzer bir metin içeren bir yapı hatası oluşturulur:

  "Proje Microsoft. NETCore. App sürüm 2.0.0 kullanılarak geri yüklendi, ancak geçerli ayarlarla sürüm 2.0.6 kullanılacak. Bu sorunu çözmek için, geri yükleme ve derleme ya da yayımlama gibi sonraki işlemler için aynı ayarların kullanıldığından emin olun. Genellikle bu sorun, Runtimeıdentifier özelliği Build veya Publish sırasında ayarlandıysa, geri yükleme sırasında olmasa da oluşabilir. "

> [!NOTE]
> `restore` ve `build` gibi başka bir komutun parçası olarak örtük bir şekilde çalıştırılabilir `publish` . Başka bir komutun parçası olarak örtük olarak çalıştırıldığında, doğru yapıtların üretilmesi için ek bağlamla birlikte sağlanır. `publish`Bir çalışma zamanı (örneğin, `dotnet publish -r linux-x64` ) kullandığınızda, `restore` Linux-x64 çalışma zamanının paketini örtülü geri yükler. `restore`Açıkça çağırırsanız, bu bağlamı içermediğinden çalışma zamanı paketlerini varsayılan olarak geri yüklemez.

## <a name="how-to-avoid-restore-during-publish"></a>Yayımlama sırasında geri yükleme nasıl önlenir

`restore`İşlemin bir parçası olarak çalıştırmak `publish` Senaryonuz için istenmeyen bir durum olabilir. `restore` `publish` Kendi içinde bulunan uygulamalar oluştururken kullanmaktan kaçınmak için aşağıdakileri yapın:

- Özelliği, `RuntimeIdentifiers` yayımlanacak tüm [RID](../rid-catalog.md) 'lerin noktalı virgülle ayrılmış bir listesine ayarlayın.
- `TargetLatestRuntimePatch`Özelliğini olarak ayarlayın `true` .

## <a name="no-restore-argument-with-dotnet-publish-options"></a>dotnet publish seçenekleriyle geri yükleme olmayan bağımsız değişken

Aynı proje dosyası ile hem kendi içinde hem de [çerçeveye bağımlı uygulamalar](index.md) oluşturmak istiyorsanız ve `--no-restore` bağımsız değişkenini ile kullanmak istiyorsanız `dotnet publish` aşağıdakilerden birini seçin:

1. Çerçeveye bağımlı davranışı tercih edin. Uygulama çerçeveye bağımlıysa, bu varsayılan davranıştır. Uygulama kendi kendine dahil ise ve düzeltme eki yüklenmemiş 2.1.0 yerel çalışma zamanını kullanıyorsa, öğesini `TargetLatestRuntimePatch` Proje dosyasında olarak ayarlayın `false` .

2. Kendi kendine içerilen davranışı tercih edin. Uygulama kendinden içeriyorsa, varsayılan davranıştır. Uygulama çerçeveye bağımlıdır ve en son düzeltme ekinin yüklü olmasını gerektiriyorsa, `TargetLatestRuntimePatch` `true` Proje dosyasında olarak ayarlayın.

3. `RuntimeFrameworkVersion`Proje dosyasındaki belirli bir düzeltme eki sürümüne ayarlayarak çalışma zamanı çerçevesi sürümünün açık denetimini alın.
