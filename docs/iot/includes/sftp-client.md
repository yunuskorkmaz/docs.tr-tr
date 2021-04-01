---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589977"
---
<span data-ttu-id="2df25-101">[BIR SFTP Istemcisi kullanarak](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), dosyaları geliştirme bilgisayarındaki yayımla konumundan Raspberry PI üzerinde yeni bir klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2df25-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="2df25-102">Örneğin, `scp` dosyaları geliştirme bilgisayarından Raspberry PI 'nize kopyalamak için komutunu kullanmak üzere, bir komut istemi açın ve aşağıdakileri yürütün:</span><span class="sxs-lookup"><span data-stu-id="2df25-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="2df25-103">Konum:</span><span class="sxs-lookup"><span data-stu-id="2df25-103">Where:</span></span>

- <span data-ttu-id="2df25-104">`-r`Seçeneği, `scp` dosyaları yinelemeli olarak kopyalamayı söyler.</span><span class="sxs-lookup"><span data-stu-id="2df25-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="2df25-105">*/Publish-location/* , önceki adımda yayımladığınız klasördür.</span><span class="sxs-lookup"><span data-stu-id="2df25-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="2df25-106">`pi@raspberypi` Kullanıcı ve ana bilgisayar adları biçimindedir `<username>@<hostname>` .</span><span class="sxs-lookup"><span data-stu-id="2df25-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="2df25-107">*/Home/Pi/Deployment-location/* , Raspberry PI üzerinde yeni klasördür.</span><span class="sxs-lookup"><span data-stu-id="2df25-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="2df25-108">En son Windows sürümlerinde, önceden yüklenmiş olan OpenSSH bulunur `scp` .</span><span class="sxs-lookup"><span data-stu-id="2df25-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>
