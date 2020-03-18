---
title: .NET Core SDK’sına genel bakış
description: .NET Core projeleri oluşturmak için kullanılan bir dizi kitaplık ve araç olan .NET Core SDK hakkında bilgi edinin.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: c2723e0e28c889f91f79ea3c0b26aa38f69fb41c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157472"
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK’sına genel bakış

.NET Core SDK, geliştiricilerin .NET Core uygulamaları ve kitaplıkları oluşturmasına olanak tanıyan bir dizi kitaplık ve araçtır. Uygulamaları oluşturmak ve çalıştırmak için kullanılan aşağıdaki bileşenleri içerir:

- .NET Çekirdek CLI.
- .NET Çekirdek kitaplıkları ve çalışma zamanı.
- `dotnet` [Sürücü.](tools/index.md#driver)

## <a name="acquiring-the-net-core-sdk"></a>.NET Çekirdek SDK'nın Satın Alınması

Herhangi bir takım olduğu gibi, ilk şey makinenize araçları almaktır. Senaryonuza bağlı olarak, Aşağıdaki yöntemlerden birini kullanarak SDK'yı yükleyebilirsiniz:

- Yerel yükleyicileri kullanın.
- Yükleme kabuğu komut dosyasını kullanın.

Yerel yükleyiciler öncelikle geliştirici makineleri içindir. SDK, desteklenen her platformun Ubuntu'daki DEB paketleri veya Windows'daki MSI paketleri gibi yerel yükleme mekanizması kullanılarak dağıtılır. Bu yükleyiciler, kullanıcının yüklemeden hemen sonra SDK'yı kullanması için gereken ortamı yükler ve ayarlar. Ancak, makineüzerinde idari ayrıcalıklar da gerektirir. [.NET indirmeler](https://dotnet.microsoft.com/download) sayfasında kurulacak SDK'yı bulabilirsiniz.

Diğer taraftan, komut dosyalarını yükleyin, yönetim ayrıcalıkları gerektirmez. Ancak, makineye herhangi bir ön koşul da yüklemezler; tüm ön koşulları el ile yüklemeniz gerekir. Komut dosyaları çoğunlukla yapı sunucuları kurmak veya yönetici ayrıcalıkları olmadan araçları yüklemek istediğinizde (yukarıdaki ön koşullar uyarıya dikkat edin) içindir. [Komut dosyası başvuru](tools/dotnet-install-script.md) makalesinde daha fazla bilgi bulabilirsiniz. SDK'yı CI build sunucunuzda nasıl kurabileceğinizle ilgileniyorsanız, [Sürekli Tümleştirme (CI) makalesinde Kullanarak .NET Core SDK ve araçları](tools/using-ci-with-cli.md) nabakını görün.

Varsayılan olarak, SDK "yan yana" (SxS) bir şekilde yükler, bu da birden çok sürümün tek bir makinede herhangi bir zamanda bir arada bulunabileceği anlamına gelir. CLI komutlarını çalıştırırken sürümün nasıl seçiliş yaptığı makaleyi [kullanmak için .NET Core sürümünü seç'te](versions/selection.md) daha ayrıntılı olarak açıklanır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI genel bakış](tools/index.md)
- [.NET Core sürüm genel bakış](versions/index.md)
- [.NET Core çalışma süresi ve SDK nasıl kaldırılır?](versions/remove-runtime-sdk-versions.md)
- [Kullanmak için .NET Core sürümünü seçin](versions/selection.md)
