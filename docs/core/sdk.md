---
title: .NET core SDK'sı genel bakış
description: Kitaplıklar ve araçlar .NET Core projeleri oluşturmak için kullanılan bir dizi olan .NET Core SDK hakkında bilgi edinin.
ms.date: 05/13/2019
ms.technology: dotnet-cli
ms.openlocfilehash: f56d7238eaaaa677db38430358ce94890632469e
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959237"
---
# <a name="net-core-sdk-overview"></a>.NET core SDK'sı genel bakış

.NET core Yazılım Geliştirme Seti (SDK), kitaplıklar ve Araçlar, geliştiricilerin, .NET Core uygulamaları ve kitaplıkları oluşturmak kümesidir. Bu, oluşturmak ve uygulamaları çalıştırmak için kullanılan aşağıdaki bileşenleri içerir:

- .NET Core CLI araçları.
- .NET core kitaplıkları ve çalışma zamanı.
- `dotnet` [Sürücü](/tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK'sını edinme

Herhangi bir araç olduğu gibi ile ilk şey araçlarını makinenize almaktır. Senaryonuza bağlı olarak, aşağıdaki yöntemlerden birini kullanarak SDK'sını yükleyebilirsiniz:

- Yerel yükleyicilerden kullanın.
- Yükleme Kabuk betiği kullanın.

Yerel yükleyicilerden öncelikle geliştiricinin makineler için yöneliktir. SDK'sı, Windows üzerinde Ubuntu veya MSI paketleri DEB paketleri gibi desteklenen her platformun yerel yükleme mekanizması kullanılarak dağıtılır. Bu yükleyicilerden yükleyin ve ortamı kullanıcının yüklendikten hemen sonra SDK'yı kullanmak gereken şekilde ayarlayın. Ancak, bunlar ayrıca makine üzerinde yönetim ayrıcalıkları gerektirir. SDK'yı yüklemek için bulabilirsiniz [.NET indirir](https://dotnet.microsoft.com/download) sayfası.

Yükleme betikleri, diğer yandan yönetici ayrıcalıkları gerektirmez. Ancak, bunlar da herhangi bir önkoşulu makinede yüklemeyin; Tüm Önkoşullar el ile yüklemeniz gerekir. Komut dosyaları çoğunlukla derleme sunucularında veya yönetici ayrıcalıkları (yukarıdaki önkoşulları uyarı unutmayın) olmadan araçları yüklemek istediğiniz zaman ayarlamak için yöneliktir. Daha fazla bilgi bulabilirsiniz [betik başvurusu yükleme](tools/dotnet-install-script.md) makalesi. CI yapı sunucunuz üzerindeki SDK'yı kurma ilginizi çekiyorsa bkz [kullanarak .NET Core SDK'sı ve araçları, sürekli tümleştirme (CI)](tools/using-ci-with-cli.md) makalesi.

Varsayılan olarak, SDK'sı CLI araçları birden çok sürümünü tek bir makinede herhangi bir belirli zamanda çalıştırılabileceği anlamına gelir "yan yana" (SxS) şekilde yüklenir. CLI komutlarını çalıştırırken sürüm nasıl çekilen daha ayrıntılı olarak açıklanan [kullanılacak .NET Core sürümünü seçin](/versions/selection.md) makalesi.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core CLI](tools/index.md)
- [.NET core sürüm genel bakış](/versions/index.md)
- [SDK ve .NET Core çalışma zamanı'nı kaldırma](versions/remove-runtime-sdk-versions.md)
- [Kullanılacak .NET Core sürümünü seçin](/versions/selection.md)
