---
title: ".NET core dağıtım paketleme"
description: "Paket, öğrenin adını ve dağıtım için .NET Core sürümü."
keywords: ".NET, .NET core, kaynak, yapı"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.workload: dotnetcore
ms.openlocfilehash: 9f5cd2f7c4fec553dfdfaf1765663b6896b3061d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-distribution-packaging"></a>.NET core dağıtım paketleme

.NET Core daha da fazla platformlarda kullanılabilir hale geldiğinde, adı, paket hakkında bilgi edinmek yararlı olacaktır ve sürümü. Bu şekilde, paket maintainers burada .NET çalıştırmak kullanıcıları seçin olsun tutarlı bir deneyim sağlamaya yardımcı olabilir.

## <a name="net-core-components"></a>.NET çekirdek bileşenleri

.NET core paketlenmesi gereken üç ana bölümden yapılır:

1. **Ana bilgisayar** (olarak da bilinen "Karıştırıcı") iki ayrı rolleri içerir: uygulamayı başlatmak için bir çalışma zamanı etkinleştirmek ve komutları ona çözümlenebilen bir SDK etkinleştirin. Ana bilgisayarın yerel bir yürütülebilir dosya olduğunu (`dotnet.exe`) ve Destek İlkesi başlatılamadığından (yüklü `host/fxr`). Koddan oluşturulmuş [ `dotnet/core-setup` ](https://github.com/dotnet/core-setup/) deposu. Yoktur genellikle yalnızca bir ana bilgisayar belirli bir makinede kesin bir gereklilik olmasa da.
2. **Framework** çalışma zamanını yapılan ve yönetilen kitaplıkları destekleme. Çerçeve, uygulamanın bir parçası olarak ya da birden çok uygulama tarafından tekrar merkezi bir konumda paylaşılan bir çerçeve olarak yüklenebilir. Herhangi bir sayıda paylaşılan çerçeveler belirli bir makinede yüklü olabilir. Paylaşılan çerçeveler Canlı altında `shared/Microsoft.NETCore.App/<version>`. Ana bilgisayar İleri düzeltme eki sürümleri arasında yapar. Bir uygulama hedefleri varsa `Microsoft.NETCore.App` 1.0.0 ve yalnızca 1.0.4 varsa, uygulama 1.0.4 karşı başlatılır.
3. **SDK** (olarak da bilinen "Araçları"), yazma ve .NET Core kitaplıkları ve uygulamaları oluşturmak için kullanılan yönetilen araç kümesidir. SDK, CLI, MSBuild, ilişkili derleme görev ve hedeflerini, NuGet, yeni proje şablonları, vb. içerir. (Daha eski bir sürümü açıkça gerektiren Örneğin, yapı projeleri için) bir makinede birden fazla SDK'ları olması mümkündür, ancak son yayımlanan araçları kullanmanız önerilir.

## <a name="recommended-package-names"></a>Önerilen paket adı

Aşağıdaki yönergeler paket adları için Bizim önerimiz verilmiştir. Bir paket Bakımcı gibi çeşitli nedenlerden üzerinde göre öğesinden farklı gelenek hedefleme belirli dağıtım ayırmak seçebilirsiniz.

### <a name="minimum-package-set"></a>Minimum paket ayarlama

* `dotnet-runtime-[major].[minor]`: (yalnızca en son düzeltme eki sürümü için belirtilen ana + ikincil birlikte olmalıdır Paket Yöneticisi'nde kullanılabilir) belirtilen sürüme sahip paylaşılan bir çerçeve. **bağımlılıklar**:`dotnet-host`
* `dotnet-sdk`: en yeni SDK'ya. **bağımlılıklar**: en son `dotnet-sdk-[major].[minor]`.
* `dotnet-sdk-[major].[minor]`: SDK'sı ile belirtilen sürümü. Böylece kullanıcılar için paylaşılan bir çerçeve kolayca bir SDK ilişkilendirebilirsiniz belirtilen sürümden yüksek dahil dahil paylaşılan çerçeveler sürümüdür. **bağımlılıklar**: `dotnet-host`, bir veya daha fazla `dotnet-runtime-[major].[minor]` (çalışma zamanları birini kullanılan SDK kodunun kendisi, diğer kullanıcıların derleyip karşı çalıştırmak İşte).
* `dotnet-host`: son ana bilgisayar.

#### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme paylaşılan framework sürümleri ve SDK'sını içerecek şekilde karar verebilirsiniz. Bu hiçbir zaman içinde sürüm bilgisi olmayan eklenmesi gereken `dotnet-sdk` paketini ancak sürümlü paketleri olarak adı birincil ve ikincil sürüm bölümlerini eklenmiş bir ek Önizleme işaretçisi ile serbest bırakılacak. Örneğin, olabilir bir `dotnet-sdk-2.0-preview-final` paketi.

### <a name="optional-additional-packages"></a>İsteğe bağlı ek paketleri

Bazı maintainers ek paketleri gibi sağlamayı tercih edebilirsiniz:

* `dotnet-lts`: paylaşılan framework'ün en son uzun süreli destek (LTS) sürümü. [Sürüm trenler LTS ve geçerli](~/docs/core/versions/lts-current.md) , .NET Core yayımlanan farklı cadences karşılık gelir. Kullanıcıların bir ya da ne sıklıkta güncelleştirmeye istekli göre diğer tren, benimsenmesi seçenekleriniz vardır. Bu ayrıca olabilir ya da kabul distro bağlı olarak anlamı olmayabilir düzeylerini desteklemek için bağlı bir kavramdır.

## <a name="disk-layout"></a>Disk düzeni

.NET Core paketleri yükleme sırasında hedef hedeflerine diskteki göreli yerleşimini önemli.
`dotnet.exe` Konak yanına yerleştirilmelidir `sdk` ve `shared` sürümü tutulan içeriğini içeren klasörleri `dotnet-sdk` SDK paketleri ve `dotnet-runtime` framework paketleri paylaşılan.

Dosya ve dizinlerin paketler içinde disk düzeni sürümlü ' dir. En son güncelleştirme yani `dotnet-runtime` önceki sürümlerinde, paket güncelleştirerek uygulamalarınız bölme olasılığını azaltmak yan yana yeni sürümü yükler. Paket güncelleştirmesi, önceki sürümler kaldırmamanız gerekir.

## <a name="update-policies"></a>Güncelleştirme ilkeleri

Zaman bir `update` olduğu gerçekleştirilecek davranışı her paket, aşağıdaki gibidir:

* `dotnet-runtime-[major].[minor]`: yeni düzeltme eki sürümleri güncelleştirme paketi, ancak yeni ikincil veya önemli sürümleri ayrı paketler.
* `dotnet-sdk`: `update` iletme birincil, ikincil ve düzeltme eki sürümleri yapar.
* `dotnet-sdk-[major].[minor]`: yeni düzeltme eki sürümleri güncelleştirme paketi, ancak yeni ikincil veya önemli sürümleri ayrı paketler.
* `dotnet-lts`: `update` iletme birincil, ikincil ve düzeltme eki sürümleri yapar.

Bu konu, .NET Core, ancak her distro sunmak için hangi sürümlerinin seçmek boş olduğu ve ne zaman paketleme bizim önerileri sunulan. Örneğin, birden fazla güncel olan değerleri kararlılık yalnızca sürümleri yayımlamayı seçebilirsiniz distro ile LTS yayın Eğitimi, ek.