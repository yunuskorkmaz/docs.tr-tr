---
title: .NET core SDK'ya genel bakış
description: Kitaplıklar ve araçlar .NET Core projeleri oluşturmak için kullanılan bir dizi olan .NET Core SDK hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: f23140166ada0c39d4267a4fd2ba5187b6c13c83
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169325"
---
# <a name="net-core-sdk-overview"></a>.NET core SDK'ya genel bakış

.NET core Yazılım Geliştirme Seti (SDK), kitaplıklar ve Araçlar, geliştiricilerin, .NET Core uygulamaları ve kitaplıkları oluşturmak kümesidir. Geliştiriciler, büyük olasılıkla alacağı paketidir. 

Bunu, aşağıdaki bileşenleri içerir:

1. Uygulamalar oluşturmak amacıyla kullanılan .NET Core komut satırı araçları
2. .NET uygulamaları hem de sağlayan çekirdek (kitaplıkları ve çalışma zamanı) oluşturulan ve çalıştırma
3. `dotnet` Çalıştırmak için sürücü [CLI komutları](tools/index.md) çalışan uygulamaların yanı sıra

## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK'sını edinme
Herhangi bir araç olduğu gibi ile ilk şey araçlarını makinenize almaktır. Senaryonuza bağlı olarak, yerel yükleyicilerden ya da SDK'sını yükleyin veya yükleme Kabuk betiği kullanmak için kullanabilirsiniz.

Yerel yükleyicilerden öncelikle geliştiricinin makineler için yöneliktir. SDK'sı, desteklenen her platformun yerel yükleme mekanizması, örneğin Windows üzerinde Ubuntu veya MSI paketleri DEB paketleri kullanılarak dağıtılır. Bu yükleyicilerden yükleyecek ve ortamı kullanıcının yüklendikten hemen sonra SDK'yı kullanmak gereken şekilde ayarlayın. Ancak, bunlar ayrıca makine üzerinde yönetim ayrıcalıkları gerektirir. Yükleme talimatlarına görüntüleyebileceğiniz [.NET Core Yükleme Kılavuzu](https://aka.ms/dotnetcoregs).

Yükleme betikleri, diğer taraftan, yönetici ayrıcalıklarına gerek yoktur. Ancak, bunlar da herhangi bir önkoşulu makineye yükleyeceğiniz değil; Tüm Önkoşullar el ile yüklemeniz gerekir. Komut dosyaları çoğunlukla derleme sunucularında veya yönetici ayrıcalıkları (yukarıdaki önkoşulları uyarı unutmayın) olmadan araçları yüklemek istediğiniz zaman ayarlamak için yöneliktir. Daha fazla bilgi bulabilirsiniz [yükleme komut dosyası başvuru konusu](tools/dotnet-install-script.md). Nasıl CI yapı sunucunuzda SDK'sını ayarlama konusunda ilgileniyorsanız göz atın [SDK CI sunucularıyla](tools/using-ci-with-cli.md) belge.

Varsayılan olarak, bir "yan yana" (SxS) şekilde SDK'yı yükler. Bu CLI araçları birden çok sürümünü tek bir makinede herhangi bir belirli zamanda çalıştırılabileceği anlamına gelir. Doğru sürümü kullanılma daha ayrıntılı olarak açıklanan [sürücü bölüm](tools/index.md#driver) konunun .NET Core komut satırı araçları.