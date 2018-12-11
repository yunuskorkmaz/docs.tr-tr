---
title: Çalışma zamanı, ileri sarma .NET Core kendi içinde uygulama dağıtımları için.
description: DotNet hakkında bilgi edinmek kendi içinde dağıtımlar için değişiklikleri yayımlayın.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: dde00cf71f0d67c8c4380748e01a4ef5c17ebb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126685"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Kendi başına dağıtım çalışma zamanı, ileri sarma

.NET core [kendi içinde uygulama dağıtımları](index.md) hem .NET Core kitaplıkları hem de .NET Core çalışma zamanı içerir. .NET Core 2.1 SDK (sürüm 2.1.300), kendi içinde uygulama dağıtımı başlatılıyor [yüksek düzeltme çalışma zamanı makinenizde yayımlar](https://github.com/dotnet/designs/pull/36). Varsayılan olarak, [ `dotnet publish` ](../tools/dotnet-publish.md) için kendi içinde bir dağıtım yayımlama makinede SDK'ın bir parçası olarak yüklenen en son sürümünü seçer. Bu güvenlik (ve diğer düzeltmeleri ile) çalıştırmak dağıtılan uygulamanızın tanır sırasında kullanılabilir `publish`. Uygulamanın yeni bir düzeltme eki elde etmek için yeniden yayımlanan olması gerekir. Kendi içindeki uygulamaları belirterek oluşturulduğunda `-r <RID>` üzerinde `dotnet publish` komutunu veya belirterek [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) proje dosyasında (csproj / vbproj) veya komut satırında.

## <a name="patch-version-roll-forward-overview"></a>Düzeltme eki sürümü Top iletme genel bakış

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) ve [ `publish` ](../tools/dotnet-publish.md) olan `dotnet` komutları ayrı olarak çalıştırabilirsiniz. Çalışma zamanı seçimi parçasıdır `restore` işlemi değil `publish` veya `build`. Eğer `publish`, en son düzeltme eki sürümü seçilir. Eğer `publish` ile `--no-restore` bağımsız değişkeni, ardından değil alabilirsiniz istenen düzeltme eki sürümü için bir önceki `restore` ilke yayımlama yeni kendi içinde uygulama yürütülmemiş olabilir değil. Bu durumda, aşağıdakine benzer bir metinle bir derleme hatası üretilir:

  "Projenin Microsoft.NETCore.App sürüm 2.0.0 kullanarak geri yüklendi ancak geçerli ayarlarla 2.0.6 sürüm yerine kullanılacak. Bu sorunu çözmek için aynı ayarları yapı gibi sonraki işlemleri ve geri yükleme için kullanılan veya yayımlama emin olun. Genellikle bu sorunu sırasında özelliği ayarlanmış RuntimeIdentifier derleme veya yayınlama ancak olmayan geri yükleme işlemi sırasında ortaya çıkabilir."

> [!NOTE]
> `restore` ve `build` başka bir komuta bir parçası olarak gibi örtük olarak çalıştırılabilir `publish`. Böylece doğru yapıtlar üretilen başka bir komutun parçası olarak örtülü olarak çalıştırdığınızda, bunlar ek bağlam ile sağlanır. Olduğunda, `publish` bir çalışma zamanı ile (örneğin, `dotnet publish -r linux-x64`), örtük `restore` x64 linux çalışma zamanı paketleri geri yükler. Eğer `restore` bu bağlamı olmadığından açıkça, çalışma zamanı paketlerini varsayılan olarak, geri yüklemez.

## <a name="how-to-avoid-restore-during-publish"></a>Geri yükleme sırasında yayımlama önlemek yapma

Çalışan `restore` parçası olarak `publish` işlemi senaryonuz için istenmeyen olabilir. Önlemek için `restore` sırasında `publish` kendi içindeki uygulamaları oluştururken, aşağıdakileri yapın:

* Ayarlama `RuntimeIdentifiers` tüm noktalı virgülle ayrılmış bir liste özelliğini [RID'ler](../rid-catalog.md) yayımlanacak.
* Ayarlama `TargetLatestRuntimePatch` özelliğini `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Hayır-geri yükleme bağımsız değişken dotnet ile yayımlama seçenekleri

Hem kendi içindeki uygulamaları oluşturmak istiyorsanız ve [framework bağımlı uygulamaları](index.md) aynı proje dosyasıyla ve kullanmak istediğiniz `--no-restore` bağımsız değişkeniyle `dotnet publish`, aşağıdakilerden birini seçin:

1. Framework bağımlı davranış tercih eder. Framework bağımlı uygulama ise varsayılan davranış budur. Uygulama kendi içinde bağımsızdır ve yüklenmemiş bir 2.1.0 kullanabilirsiniz yerel çalışma zamanının `TargetLatestRuntimePatch` için `false` proje dosyasındaki.

2. Müstakil davranışı tercih eder. Bu, uygulamanın kendi içinde ise, varsayılan davranıştır. Uygulama framework bağlıdır ve yüklü en son düzeltme eki verilirse `TargetLatestRuntimePatch` için `true` proje dosyasındaki.

3. Açık çalışma zamanı framework sürümü ayarlayarak denetimini `RuntimeFrameworkVersion` proje dosyasındaki belirli bir düzeltme eki sürümü için.
