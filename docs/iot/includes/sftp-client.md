---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "96589977"
---
[BIR SFTP Istemcisi kullanarak](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), dosyaları geliştirme bilgisayarındaki yayımla konumundan Raspberry PI üzerinde yeni bir klasöre kopyalayın.

Örneğin, `scp` dosyaları geliştirme bilgisayarından Raspberry PI 'nize kopyalamak için komutunu kullanmak üzere, bir komut istemi açın ve aşağıdakileri yürütün:

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

Konum:

- `-r`Seçeneği, `scp` dosyaları yinelemeli olarak kopyalamayı söyler.
- */Publish-location/* , önceki adımda yayımladığınız klasördür.
- `pi@raspberypi` Kullanıcı ve ana bilgisayar adları biçimindedir `<username>@<hostname>` .
- */Home/Pi/Deployment-location/* , Raspberry PI üzerinde yeni klasördür.

> [!TIP]
> En son Windows sürümlerinde, önceden yüklenmiş olan OpenSSH bulunur `scp` .
