---
title: .NET Core SDK’sına genel bakış
description: .NET Core projeleri oluşturmak için kullanılan bir dizi kitaplık ve araç olan .NET Core SDK hakkında bilgi edinin.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 7eb06e4fd94ed2a73af2741e98e21e02728c27e4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595747"
---
# <a name="net-core-sdk-overview"></a>.NET Core SDK’sına genel bakış

.NET Core SDK, geliştiricilerin .NET Core Uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplıklar ve araçlar kümesidir. Uygulama derlemek ve çalıştırmak için kullanılan aşağıdaki bileşenleri içerir:

- .NET Core CLI.
- .NET Core kitaplıkları ve çalışma zamanı.
- `dotnet` [Sürücü](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK alınıyor

Herhangi bir araç ile olduğu gibi, ilk şey makinenize araçları almak için kullanılır. Senaryonuza bağlı olarak, aşağıdaki yöntemlerden birini kullanarak SDK 'Yı yükleyebilirsiniz:

- Yerel yükleyicileri kullanın.
- Yükleme kabuğu betiğini kullanın.

Yerel yükleyiciler öncelikle geliştirici makinelerine yöneliktir. SDK, Windows üzerinde Ubuntu veya MSI paketlerinde DEB paketleri gibi desteklenen her platformun yerel yüklemesi mekanizması kullanılarak dağıtılır. Bu yükleyiciler, kullanıcının yüklemeden hemen sonra SDK 'Yı kullanması için gerektiğinde ortamı yükler ve ayarlar. Ancak, makine üzerinde yönetici ayrıcalıklarına de gereksinim duyar. [.Net İndirmeleri](https://dotnet.microsoft.com/download) sayfasına yüklemek için SDK 'yı bulabilirsiniz.

Diğer yandan, yönetim ayrıcalıkları gerektirmeyen betikleri yükler. Bununla birlikte, makineye hiçbir önkoşul de yüklemez; tüm önkoşulları el ile yüklemeniz gerekir. Betikler genellikle derleme sunucularını ayarlamak için veya araçları yönetici ayrıcalıkları olmadan yüklemek istediğinizde (yukarıdaki önkoşulları desteklenmediği uyarısıyla). Daha fazla bilgi için [komut dosyası başvurusunu yükleyebilirsiniz](tools/dotnet-install-script.md) makalesine ulaşabilirsiniz. CI yapı sunucunuzda SDK 'Yı ayarlama hakkında bilgi edinmek istiyorsanız [sürekli tümleştirme (CI) makalesinde .NET Core SDK ve araçları kullanma](tools/using-ci-with-cli.md) makalesine bakın.

SDK varsayılan olarak "yan yana" (SxS) şekilde yüklenir. Bu, birden fazla sürümün tek bir makinede belirli bir zamanda bir arada olması anlamına gelir. CLı komutlarını çalıştırırken sürümün nasıl çekilmesi, [kullanılacak .NET Core sürümünü Seç](versions/selection.md) makalesinde daha ayrıntılı olarak açıklanmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI’ya genel bakış](tools/index.md)
- [.NET Core sürüm oluşturmaya genel bakış](versions/index.md)
- [.NET Core çalışma zamanı ve SDK 'sını kaldırma](install/remove-runtime-sdk-versions.md)
- [Kullanılacak .NET Core sürümünü seçin](versions/selection.md)
