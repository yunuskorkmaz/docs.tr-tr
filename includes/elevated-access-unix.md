---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540128"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="50106-101">Genel aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="50106-101">Install the global tool</span></span>

<span data-ttu-id="50106-102">Bir korumalı konumu kullanarak paket varlıklar yüklenmelidir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="50106-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="50106-103">Bu ayrım, kısıtlı kullanıcı ortamını ile yükseltilmiş bir ortam paylaşımı önler.</span><span class="sxs-lookup"><span data-stu-id="50106-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="50106-104">`/usr/local/share/dotnet-tools` izinle oluşturulacak `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="50106-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="50106-105">Dizin zaten varsa, kullanmak `ls -l` kısıtlı kullanıcı dizini düzenleme izni yoksa doğrulamak için komutu.</span><span class="sxs-lookup"><span data-stu-id="50106-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="50106-106">Bu durumda, kullanın `sudo chmod o-w -R /usr/share/dotnet-tools` erişimi kaldırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="50106-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="50106-107">Genel aracı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="50106-107">Run the global tool</span></span>

<span data-ttu-id="50106-108">**1. seçenek** sudo ile tam yolu kullanın:</span><span class="sxs-lookup"><span data-stu-id="50106-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="50106-109">**2. seçenek** aracının her aracı için bir kez sembol bağlantı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="50106-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="50106-110">Ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="50106-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="50106-111">Genel Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="50106-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="50106-112">Sembol bağlantı yaptıysanız de kaldırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="50106-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
