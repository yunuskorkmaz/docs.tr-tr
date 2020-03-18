---
title: .NET Core bağımsız uygulama dağıtımları için çalışma zamanı ileri sarma.
description: Bağımsız dağıtımlar için dotnet yayımlama değişiklikleri hakkında bilgi edinin.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 22385c7b5d2bf87755fd51cd6268d21fe3431c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740789"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Kendi içinde dağıtım çalışma zamanını ileri sarma

.NET Core [bağımsız uygulama dağıtımları](index.md) hem .NET Core kitaplıklarını hem de .NET Core çalışma süresini içerir. .NET Core 2.1 SDK'dan (sürüm 2.1.300) başlayarak, bağımsız bir uygulama dağıtımı [makinenizdeki en yüksek yama çalışma süresini yayımlar.](https://github.com/dotnet/designs/pull/36) Varsayılan olarak, [`dotnet publish`](../tools/dotnet-publish.md) bağımsız bir dağıtım için yayımlama makinesinde SDK'nın bir parçası olarak yüklenen en son sürümü seçer. Bu, dağıtılmış uygulamanızın `publish`sırasında kullanılabilen güvenlik düzeltmeleri (ve diğer düzeltmeler) ile çalışmasını sağlar. Yeni bir yama edinmek için uygulamanın yeniden yayımlanmış olması gerekir. Bağımsız uygulamalar `-r <RID>` `dotnet publish` komutüzerinde belirterek veya proje dosyasında (csproj / vbproj) veya komut satırında çalışma zamanı [tanımlayıcısı (RID)](../rid-catalog.md) belirtilmek suretiyle oluşturulur.

## <a name="patch-version-roll-forward-overview"></a>Yama sürümü roll forward genel bakış

[`restore`](../tools/dotnet-restore.md)ve [`build`](../tools/dotnet-build.md) [`publish`](../tools/dotnet-publish.md) ayrı `dotnet` ayrı çalıştırılabilen komutlardır. Çalışma zamanı seçimi işlemin `restore` bir parçasıdır, değil `publish` veya `build`. Ararsanız, `publish`en son yama sürümü seçilir. Bağımsız değişkenle birlikte ararsanız, `publish` önceki bir önce `restore` yeni bağımsız uygulama yayımlama ilkesiyle yürütülmemiş olabileceğinden, istenen yama sürümünü alamayabilirsiniz. `--no-restore` Bu durumda, aşağıdakilere benzer bir metinle bir yapı hatası oluşturulur:

  "Proje Microsoft.NETCore.App sürüm 2.0.0 kullanılarak geri yüklendi, ancak geçerli ayarları ile, sürüm 2.0.6 yerine kullanılacak. Bu sorunu gidermek için, aynı ayarların geri yükleme ve yapı veya yayımlama gibi sonraki işlemler için kullanıldığından emin olun. RuntimeIdentifier özelliği yapı veya yayımlama sırasında ayarlanır, ancak geri yükleme sırasında değil, genellikle bu sorun oluşabilir."

> [!NOTE]
> `restore`gibi `build` başka bir komutun parçası olarak `publish`dolaylı olarak çalıştırılabilir. Başka bir komutun parçası olarak dolaylı olarak çalıştırıldığında, doğru yapılar üretilebilmek için ek bağlam sağlanır. Bir `publish` çalışma zamanı ile (örneğin, `dotnet publish -r linux-x64`), `restore` örtülü linux-x64 çalışma zamanı için paketleri geri yükler. Açıkça ararsanız, `restore` bu içeriğe sahip olmadığından, varsayılan olarak çalışma zamanı paketlerini geri yüklemez.

## <a name="how-to-avoid-restore-during-publish"></a>Yayımlama sırasında geri yüklemeden nasıl kaçınıla

İşlemin bir `restore` `publish` parçası olarak çalıştırmak senaryonuz için istenmeyen bir şey olabilir. Bağımsız `restore` uygulamalar `publish` oluştururken kaçınmak için aşağıdakileri yapın:

- `RuntimeIdentifiers` Özelliği, yayımlanacak tüm [RID'lerin](../rid-catalog.md) yarı sütunlu ayrılmış listesine ayarlayın.
- Özelliği `TargetLatestRuntimePatch` ' `true`ye ayarlayın.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>dotnet yayımlama seçenekleriyle geri yükleme bağımsız değişkeni yok

Aynı proje dosyasıyla hem bağımsız uygulamalar hem de [çerçevebağımlı uygulamalar](index.md) oluşturmak istiyorsanız ve bağımsız `--no-restore` değişkeni kullanmak `dotnet publish`istiyorsanız, aşağıdakilerden birini seçin:

1. Çerçeveye bağımlı davranışı tercih edin. Uygulama çerçeveye bağlıysa, bu varsayılan davranıştır. Uygulama bağımsızsa ve yamasız 2.1.0 yerel çalışma saatini kullanabiliyorsa, proje dosyasında `TargetLatestRuntimePatch` ayarlayın. `false`

2. Kendi kendine yeten davranışı tercih edin. Uygulama bağımsızsa, bu varsayılan davranıştır. Uygulama çerçeveye bağlıysa ve proje `TargetLatestRuntimePatch` `true` dosyasında ayarlanan en son yama yüklüyse.

3. Proje dosyasındaki belirli yama sürümüne ayarlayarak `RuntimeFrameworkVersion` çalışma zamanı çerçeve sürümü üzerinde açık denetim edin.
