---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540128"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="af9c9-101">Genel aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="af9c9-101">Install the global tool</span></span>

<span data-ttu-id="af9c9-102">Paket varlıkları `--tool-path` seçeneği kullanılarak korunan bir konuma yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="af9c9-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="af9c9-103">Bu ayırma, kısıtlı bir kullanıcı ortamını yükseltilmiş bir ortamla paylaşmayı önler.</span><span class="sxs-lookup"><span data-stu-id="af9c9-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="af9c9-104">`/usr/local/share/dotnet-tools`izni `drwxr-xr-x`ile oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="af9c9-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="af9c9-105">Dizin zaten varsa, kısıtlı `ls -l` kullanıcının dizini yönetme izni olmadığını doğrulamak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="af9c9-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="af9c9-106">Bu öyleyse, `sudo chmod o-w -R /usr/share/dotnet-tools` erişimi kaldırmak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="af9c9-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="af9c9-107">Genel aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="af9c9-107">Run the global tool</span></span>

<span data-ttu-id="af9c9-108">**Seçenek 1** Sudo ile tam yolu kullanın:</span><span class="sxs-lookup"><span data-stu-id="af9c9-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="af9c9-109">**Seçenek 2** Aracın sembol bağlantısını, araç başına bir kez ekleyin:</span><span class="sxs-lookup"><span data-stu-id="af9c9-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="af9c9-110">Ve ile çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="af9c9-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="af9c9-111">Genel aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="af9c9-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="af9c9-112">Bir sembol bağlantısı yaptıysanız, bunu kaldırmanız da gerekir:</span><span class="sxs-lookup"><span data-stu-id="af9c9-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
