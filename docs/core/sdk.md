---
title: ".NET core SDK genel bakış"
description: "Bir dizi kitaplıkları ve .NET Core proje oluşturmak için kullanılan araçlar olduğu .NET Core SDK hakkında bilgi edinin."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.workload: dotnetcore
ms.openlocfilehash: f32f4c50f5b3fef8f38560ea3516265f7a4ac008
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-sdk-overview"></a>.NET core SDK genel bakış 

## <a name="introduction"></a>Giriş
.NET core Yazılım Geliştirme Seti (SDK), kitaplıklar ve .NET Core uygulamaları ve kitaplıkları oluşturmak geliştiriciler izin araçları kümesidir. Bu, geliştiricilerin büyük olasılıkla alacağı paketidir. 

Aşağıdaki bileşenleri içerir:

1. Uygulamaları oluşturmak için kullanılan .NET Core komut satırı araçları
2. .NET uygulamaları hem sağlayan çekirdek (kitaplıkları ve çalışma zamanı) oluşturulmuş ve çalıştırma
3. `dotnet` Çalıştırmak için sürücü [CLI komutları](tools/index.md) çalışan uygulamalar yanı sıra


## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK alınıyor
Herhangi bir araç olduğu gibi ile ilk şey makinenize araçları elde etmektir. Senaryonuza bağlı olarak, yükleme Kabuk betiği SDK'yı yüklemeyi veya kullanmayı yerel yükleyicileri ya da kullanabilirsiniz.

Yerel yükleyicileri Geliştirici makineler için öncelikle yöneliktir. SDK, desteklenen her platformun yerel yükleme mekanizması, örneğin Windows Ubuntu veya MSI paketleri DEB paketleri kullanılarak dağıtılır. Bu yükleyiciler yükleyin ve kullanıcının yüklendikten hemen sonra SDK'yı kullanmak gerektiği şekilde ortamını ayarlama. Ancak, bunlar ayrıca makine üzerinde yönetim ayrıcalıkları gerektirir. Yükleme yönergeleri görüntüleyebilirsiniz [.NET Core Yükleme Kılavuzu'na](https://aka.ms/dotnetcoregs).

Komut dosyaları, diğer yandan yüklemek için yönetici ayrıcalıkları gerektirmez. Ancak, bunlar ayrıca herhangi bir önkoşulu makinede yüklenmez; tüm önkoşulları el ile yüklemeniz gerekir. Komut dosyaları çoğunlukla yapı sunucuları veya yönetici ayrıcalıkları (yukarıdaki Önkoşullar uyarısıyla unutmayın) olmadan araçları yüklemek istediğiniz zaman ayarlamak için yöneliktir. Daha fazla bilgi bulabilirsiniz [betik başvuru konusu yüklemek](tools/dotnet-install-script.md). CI derleme sunucunuzda SDK ayarlamak nasıl ilgileniyorsanız bir göz atalım [CI sunucularıyla SDK](tools/using-ci-with-cli.md) belge. 

Varsayılan olarak, bir "yan yana" (SxS) şekilde SDK'sını yükler. Başka bir deyişle, CLI araçlarını birden fazla sürümünü herhangi bir zamanda tek bir makinede konumunda bulunabilir. ' In doğru sürümü kullanılma daha ayrıntılı olarak açıklanmıştır [sürücü bölüm](tools/index.md#driver) .NET Core komut satırı araçları konunun.
