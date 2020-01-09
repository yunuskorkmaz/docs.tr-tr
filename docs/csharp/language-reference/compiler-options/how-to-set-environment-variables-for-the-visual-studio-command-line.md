---
title: Visual Studio Komut Satırı için ortam değişkenlerini ayarlama
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342359"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="5b0c8-102">Visual Studio Komut Satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="5b0c8-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="5b0c8-103">VsDevCmd. bat dosyası, komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="5b0c8-104">Visual Studio 2015 ve önceki sürümleri, aynı amaçla VsDevCmd. bat değil, VSVARS32. bat kullandı.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="5b0c8-105">Bu dosya \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools veya Program Files (x86) \Microsoft Visual Studio\\*Version*\Common7\Tools. ' de depolandı</span><span class="sxs-lookup"><span data-stu-id="5b0c8-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="5b0c8-106">Visual Studio 'nun geçerli sürümü, Visual Studio 'nun önceki bir sürümüne de sahip olan bir bilgisayarda yüklüyse, VsDevCmd. bat ve VSVARS32 kullanmamalısınız. Aynı komut Istemi penceresindeki farklı sürümlerden BAT.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="5b0c8-107">Bunun yerine, her sürüm için komutunu kendi penceresinde çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="5b0c8-108">VsDevCmd. BAT dosyasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5b0c8-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="5b0c8-109">**Başlangıç** menüsünde **VS 2019 için geliştirici komut istemi**açın.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="5b0c8-110">**Visual Studio 2019** klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="5b0c8-111">Yüklemenizin \Common7\Tools alt dizinini *sunan*\Common7\Tools veya \Program Files (x86) \Microsoft Visual Studio\\*Sürüm*\\*sunan*\Program Files\Microsoft Visual Studio\\\\*sürümüne* geçin.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="5b0c8-112">(*Sürüm* , geçerli sürüm için *2019* .</span><span class="sxs-lookup"><span data-stu-id="5b0c8-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="5b0c8-113">*Teklif* , *Enterprise*, *Professional* veya *Community*'den biridir.)</span><span class="sxs-lookup"><span data-stu-id="5b0c8-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="5b0c8-114">**Vsdevcmd. bat dosyasını vsdevcmd**yazarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="5b0c8-115">VsDevCmd. bat bilgisayardan bilgisayara farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="5b0c8-116">Eksik veya hasarlı bir VsDevCmd. bat dosyasını başka bir bilgisayardan VsDevCmd. bat ile değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="5b0c8-117">Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="5b0c8-118">VsDevCmd. BAT için kullanılabilir seçenekler</span><span class="sxs-lookup"><span data-stu-id="5b0c8-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="5b0c8-119">VsDevCmd. BAT için kullanılabilir seçenekleri görmek için, `-help` seçeneğiyle komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5b0c8-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="5b0c8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b0c8-120">See also</span></span>

- [<span data-ttu-id="5b0c8-121">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="5b0c8-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
