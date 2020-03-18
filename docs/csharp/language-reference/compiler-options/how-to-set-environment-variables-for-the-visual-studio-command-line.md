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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342359"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="d6697-102">Visual Studio Komut Satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="d6697-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="d6697-103">VsDevCmd.bat dosyası komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d6697-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="d6697-104">Visual Studio 2015 ve önceki sürümlerde vsdevcmd.bat değil, aynı amaç için VSVARS32.bat kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d6697-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="d6697-105">Bu dosya \Program Files\Microsoft Visual\\Studio*Version*\Common7\Tools veya Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools'ta depolandı.</span><span class="sxs-lookup"><span data-stu-id="d6697-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="d6697-106">Visual Studio'nun geçerli sürümü Visual Studio'nun daha önceki bir sürümüne sahip bir bilgisayara yüklenmişse, VsDevCmd.bat ve VSVARS32'yi çalıştırmamalısınız. Aynı Komut İstem penceresinde farklı sürümlerden BAT.</span><span class="sxs-lookup"><span data-stu-id="d6697-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="d6697-107">Bunun yerine, her sürüm için komutu kendi penceresinde çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6697-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="d6697-108">VsDevCmd.BAT çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d6697-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="d6697-109">**Başlat** menüsünden VS **2019 için Geliştirici Komut Komut Ustem'ini**açın.</span><span class="sxs-lookup"><span data-stu-id="d6697-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="d6697-110">**Visual Studio 2019** klasöründe.</span><span class="sxs-lookup"><span data-stu-id="d6697-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="d6697-111">\Program Files\Microsoft Visual Studio\\*Sürüm*\\*Sunusu*\\\Common7\Tools veya \Program Files (x86)\Microsoft Visual Studio*Sürüm*\\*Sunan*\Common7\Tools alt dizini yüklemenizi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d6697-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="d6697-112">(*Sürüm* geçerli sürüm için *2019'dur.*</span><span class="sxs-lookup"><span data-stu-id="d6697-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="d6697-113">*Sunan* *kurumsal*biridir , *Profesyonel* veya *Topluluk*.)</span><span class="sxs-lookup"><span data-stu-id="d6697-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="d6697-114">**VsDevCmd yazarak VsDevCmd.bat**çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6697-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="d6697-115">VsDevCmd.bat bilgisayardan bilgisayara değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d6697-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="d6697-116">Eksik veya hasarlı Bir VsDevCmd.bat dosyalarını başka bir bilgisayardan bir VsDevCmd.bat ile değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="d6697-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="d6697-117">Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d6697-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="d6697-118">VsDevCmd.BAT için kullanılabilir seçenekler</span><span class="sxs-lookup"><span data-stu-id="d6697-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="d6697-119">VsDevCmd.BAT için kullanılabilir seçenekleri görmek için komutu seçeneğiyle çalıştırın: `-help`</span><span class="sxs-lookup"><span data-stu-id="d6697-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="d6697-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6697-120">See also</span></span>

- [<span data-ttu-id="d6697-121">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="d6697-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
