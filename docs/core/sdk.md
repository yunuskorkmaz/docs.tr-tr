---
title: .NET SDK genel bakış
description: .NET projeleri oluşturmak için kullanılan bir dizi kitaplık ve araç olan .NET SDK hakkında bilgi edinin.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 5236d4abec5dcbf950059dd906958158cfb592fe
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216147"
---
# <a name="net-sdk-overview"></a>.NET SDK genel bakış

.NET SDK, geliştiricilerin .NET uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplık ve araç kümesidir. Uygulama derlemek ve çalıştırmak için kullanılan aşağıdaki bileşenleri içerir:

- .NET CLı.
- .NET kitaplıkları ve çalışma zamanı.
- `dotnet` [Sürücü](tools/index.md#driver).

## <a name="acquiring-the-net-sdk"></a>.NET SDK 'Yı edinme

Herhangi bir araç ile olduğu gibi, ilk şey makinenize araçları almak için kullanılır. Senaryonuza bağlı olarak, aşağıdaki yöntemlerden birini kullanarak SDK 'Yı yükleyebilirsiniz:

- Yerel yükleyicileri kullanın.
- Yükleme kabuğu betiğini kullanın.

Yerel yükleyiciler öncelikle geliştirici makinelerine yöneliktir. SDK, Windows üzerinde Ubuntu veya MSI paketlerinde DEB paketleri gibi desteklenen her platformun yerel yüklemesi mekanizması kullanılarak dağıtılır. Bu yükleyiciler, kullanıcının yüklemeden hemen sonra SDK 'Yı kullanması için gerektiğinde ortamı yükler ve ayarlar. Ancak, makine üzerinde yönetici ayrıcalıklarına de gereksinim duyar. [.Net İndirmeleri](https://dotnet.microsoft.com/download) sayfasına yüklemek için SDK 'yı bulabilirsiniz.

Diğer yandan, yönetim ayrıcalıkları gerektirmeyen betikleri yükler. Bununla birlikte, makineye hiçbir önkoşul de yüklemez; tüm önkoşulları el ile yüklemeniz gerekir. Betikler genellikle derleme sunucularını ayarlamak için veya araçları yönetici ayrıcalıkları olmadan yüklemek istediğinizde (yukarıdaki önkoşulları desteklenmediği uyarısıyla). Daha fazla bilgi için [komut dosyası başvurusunu yükleyebilirsiniz](tools/dotnet-install-script.md) makalesine ulaşabilirsiniz. CI yapı sunucunuzda SDK 'Yı ayarlama hakkında bilgi edinmek istiyorsanız, bkz. [.NET SDK ve araçlar 'ı sürekli tümleştirme (CI) makalesinde kullanma](tools/using-ci-with-cli.md) .

SDK varsayılan olarak "yan yana" (SxS) şekilde yüklenir. Bu, birden fazla sürümün tek bir makinede belirli bir zamanda bir arada olması anlamına gelir. CLı komutlarını çalıştırırken sürümün nasıl çekilmesi, [kullanılacak .NET sürümünü Seç](versions/selection.md) makalesinde daha ayrıntılı olarak açıklanmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET CLı genel bakış](tools/index.md)
- [.NET sürüm oluşturmaya genel bakış](versions/index.md)
- [.NET çalışma zamanını ve SDK 'sını kaldırma](install/remove-runtime-sdk-versions.md)
- [Kullanılacak .NET sürümünü seçin](versions/selection.md)
