---
title: 'Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama'
ms.date: 09/29/2017
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
ms.openlocfilehash: 9b26f6b80488ad4043054cd23f0f351773e8d6d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602862"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="c72b5-102">Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c72b5-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="c72b5-103">VsDevCmd. bat dosyası, komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c72b5-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="c72b5-104">VsDevCmd. bat dosyası, Visual Studio 2017 ile sunulan yeni bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="c72b5-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="c72b5-105">Visual Studio 2015 ve önceki sürümleri, VSVARS32. bat ' i aynı amaçla kullandı.</span><span class="sxs-lookup"><span data-stu-id="c72b5-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="c72b5-106">Bu dosya \Program Files\Microsoft\\Visual Studio*Version*\Common7\Tools veya Program Files (x86) \Microsoft Visual Studio\\*Version*\Common7\Tools. içinde depolandı</span><span class="sxs-lookup"><span data-stu-id="c72b5-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="c72b5-107">Visual Studio 'nun geçerli sürümü, Visual Studio 'nun önceki bir sürümüne de sahip olan bir bilgisayarda yüklüyse, VsDevCmd. bat ve VSVARS32 kullanmamalısınız. Aynı komut Istemi penceresindeki farklı sürümlerden BAT.</span><span class="sxs-lookup"><span data-stu-id="c72b5-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="c72b5-108">Bunun yerine, her sürüm için komutunu kendi penceresinde çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c72b5-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="c72b5-109">VsDevCmd. BAT dosyasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c72b5-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="c72b5-110">**Başlangıç** menüsünde **VS 2017 için geliştirici komut istemi**açın.</span><span class="sxs-lookup"><span data-stu-id="c72b5-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="c72b5-111">**Visual Studio 2017** klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="c72b5-111">It's in the **Visual Studio 2017** folder.</span></span>

2. <span data-ttu-id="c72b5-112">\Program Files\Microsoft Visual\\Studio*Sürüm*\\*teklifi*\Common7\Tools veya \Program Files (x86) \Microsoft Visual\\Studio*Sürüm*\\teklifini değiştirinYüklemenizin \Common7\Tools alt dizini.</span><span class="sxs-lookup"><span data-stu-id="c72b5-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="c72b5-113">(*Sürüm* , geçerli sürüm için *2017* .</span><span class="sxs-lookup"><span data-stu-id="c72b5-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="c72b5-114">*Teklif* , *Enterprise*, *Professional* veya *Community*'den biridir.)</span><span class="sxs-lookup"><span data-stu-id="c72b5-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="c72b5-115">Vsdevcmd. bat dosyasını **vsdevcmd**yazarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c72b5-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="c72b5-116">VsDevCmd. bat bilgisayardan bilgisayara farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c72b5-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="c72b5-117">Eksik veya hasarlı bir VsDevCmd. bat dosyasını başka bir bilgisayardan VsDevCmd. bat ile değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c72b5-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="c72b5-118">Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c72b5-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="c72b5-119">VsDevCmd. BAT için kullanılabilir seçenekler</span><span class="sxs-lookup"><span data-stu-id="c72b5-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="c72b5-120">Vsdevcmd. bat için kullanılabilir seçenekleri görmek için komutunu `-help` seçeneğiyle çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c72b5-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="c72b5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c72b5-121">See also</span></span>

- [<span data-ttu-id="c72b5-122">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="c72b5-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
