---
title: Kendi içinde bulunan dağıtım çalışma zamanı İleri alma
description: DotNet hakkında bilgi edinin değişiklikleri müstakil dağıtımlar için yayımlayın.
author: jralexander
ms.author: kdollard
ms.date: 05/31/2018
ms.openlocfilehash: 39a23917dec1aba5142839265c555da5c1e6f09c
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071038"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Kendi içinde bulunan dağıtım çalışma zamanı İleri alma

.NET core [kendi içinde bulunan uygulama dağıtımları](index.md) .NET Core kitaplıkları ve .NET çekirdeği çalışma zamanı içerir. .NET Core SDK 2.1.300 (.NET Core 2.1), kendi içinde bulunan uygulama dağıtımı içinde başlangıç [en yüksek düzeltme eki çalışma zamanı makinenizde yayımlar](https://github.com/dotnet/designs/pull/36). Varsayılan olarak, [ `dotnet publish` ](../tools/dotnet-publish.md) için kendi içinde bulunan bir dağıtım yayımlama makinede SDK'ın bir parçası olarak yüklenen en son sürümü seçer. Bu güvenlik (ve diğer düzeltmeleri ile) çalıştırmak, dağıtılan bir uygulama sağlar sırasında kullanılabilir `publish`. Uygulamanın yeni bir düzeltme eki elde etmek için yeniden yayımlanan olması gerekir. Kendi içinde bulunan uygulamaları belirterek oluşturulduğunda `-r <RID>` üzerinde `dotnet publish` komutunu veya belirterek [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) proje dosyasında (csproj / vbproj) veya komut satırında.

## <a name="patch-version-roll-forward-overview"></a>Düzeltme eki sürümü toplama iletme genel bakış

[`restore`](../tools/dotnet-restore.md), [ `build` ](../tools/dotnet-build.md) ve [ `publish` ](../tools/dotnet-publish.md) olan `dotnet` ayrı olarak çalıştırabilirsiniz komutları. Çalışma zamanı seçimi parçası olan `restore` işlemi, değil `publish` veya `build`. Çağırırsanız `publish`, en son düzeltme eki sürümü seçilir. Çağırırsanız `publish` ile `--no-restore` bağımsız değişkeni, ardından değil alabilirsiniz istenen düzeltme eki sürümü çünkü bir önceki `restore` İlkesi yayımlama yeni kendi içinde bulunan uygulama yürütülmemiş olabilir değil. Bu durumda, bir derleme hatası aşağıdakine benzer bir metin ile oluşturulur:

  "Projeyi Microsoft.NETCore.App sürüm 2.0.0 kullanılarak geri yüklendi ancak geçerli ayarlarla sürüm 2.0.6 yerine kullanılır. Bu sorunu çözmek için aynı ayarları gibi yapı sonraki işlemleri ve geri yükleme için kullanılan veya yayımlama emin olun. Genellikle bu sorun özelliği sırasında ayarlanır RuntimeIdentifier yapı veya yayımlama ancak geri yükleme sırasında değil oluşabilir."

> [!NOTE]
> `restore` ve `build` örtük olarak başka bir komutun bir parçası olarak gibi çalıştırılabilir `publish`. Böylece doğru yapıları üretilen örtük olarak başka bir komutun parçası olarak çalıştırdığınızda, bunlar ek içerikle sağlanır. Olduğunda, `publish` bir çalışma zamanı (örneğin, `dotnet publish -r linux-x64`), örtük `restore` linux x64 çalışma zamanı için paketler geri yükler. Çağırırsanız `restore` bu bağlamı olmadığından açıkça, çalışma zamanı paketleri varsayılan olarak, geri yüklemez.

## <a name="how-to-avoid-restore-during-publish"></a>Yayımlama sırasında geri yükleme önleme

Çalışan `restore` parçası olarak `publish` işlemi senaryonuz için istenmeyen olabilir. Önlemek için `restore` sırasında `publish` müstakil uygulamaları oluştururken, aşağıdakileri yapın:

* Ayarlama `RuntimeIdentifiers` , tüm noktalı virgülle ayrılmış listesini özelliğine [RID](../rid-catalog.md) yayımlanacak.
* Ayarlama `TargetLatestRuntimePatch` özelliğine `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Hayır geri yükleme bağımsız değişken dotnet ile yayınlama seçeneklerini

Her iki kendi içinde bulunan uygulamalar oluşturmak istiyorsanız ve [framework bağımlı uygulamaları](index.md) aynı proje dosyası ile ve kullanmak istediğiniz `--no-restore` bağımsız değişkeniyle `dotnet publish`, aşağıdakilerden birini seçin:

1. Framework bağımlı davranış tercih eder. Uygulama framework bağımlı ise varsayılan davranış budur. Uygulama kendi içinde yer alan ve düzeltme eki yüklenmemiş 2.1.0 kullanabilirsiniz yerel çalışma zamanı ayarlamak `TargetLatestRuntimePatch` için `false` proje dosyasında.

2. Kendi içinde bulunan davranışı tercih eder. Bu, uygulamanın kendi içinde bulunan ise, varsayılan davranıştır. Uygulama framework bağlıdır ve en son düzeltme eki yüklenmemiş gerektiriyorsa, ayarlamak `TargetLatestRuntimePatch` için `true` proje dosyasında.

3. Açık çalışma zamanı framework sürümü ayarlayarak denetimini `RuntimeFrameworkVersion` belirli düzeltme eki sürümü proje dosyası '.
