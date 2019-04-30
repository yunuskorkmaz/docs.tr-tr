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
ms.openlocfilehash: 9eea7f76d386816aad060e9b99cea6b906a09ab9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662848"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="5ccde-102">Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="5ccde-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="5ccde-103">VsDevCmd.bat dosya komut satırı derlemeleri etkinleştirmek için uygun ortam değişkenlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ccde-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="5ccde-104">Visual Studio 2017 ile sunulan yeni bir dosya VsDevCmd.bat dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="5ccde-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="5ccde-105">Visual Studio 2015 ve önceki sürümleri VSVARS32.bat aynı amaçla kullanılan.</span><span class="sxs-lookup"><span data-stu-id="5ccde-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="5ccde-106">Bu dosya, \Program Files\Microsoft Visual Studio depolanmış\\*sürüm*\Common7\Tools veya Program dosyaları (x86) \Microsoft Visual Studio\\*sürüm*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="5ccde-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="5ccde-107">Visual Studio'nun geçerli sürümü Visual Studio'nun önceki bir sürümü olan bir bilgisayarda yüklü ise, VsDevCmd.bat ve VSVARS32 çalıştırmamanız gerekir. Aynı komut istemi penceresinde farklı sürümlerine ait BAT.</span><span class="sxs-lookup"><span data-stu-id="5ccde-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="5ccde-108">Bunun yerine, kendi penceresinde her sürüm için komutu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ccde-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="5ccde-109">VsDevCmd.BAT çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5ccde-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="5ccde-110">Gelen **Başlat** menüsünde, açık **VS 2017 için geliştirici komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="5ccde-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="5ccde-111">İçinde **Visual Studio 2017** klasör.</span><span class="sxs-lookup"><span data-stu-id="5ccde-111">It's in the **Visual Studio 2017** folder.</span></span>

2. <span data-ttu-id="5ccde-112">Değiştirme \Program Visual Studio'ya\\*sürüm*\\*sunan*\Common7\Tools veya \Program dosyaları (x86) \Microsoft Visual Studio\\ *Sürüm*\\*sunan*yüklemenizin \Common7\Tools alt dizinine geçin.</span><span class="sxs-lookup"><span data-stu-id="5ccde-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="5ccde-113">(*Sürüm* olduğu *2017* geçerli sürümü için.</span><span class="sxs-lookup"><span data-stu-id="5ccde-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="5ccde-114">*Teklif* biri *Kurumsal*, *Professional* veya *topluluk*.)</span><span class="sxs-lookup"><span data-stu-id="5ccde-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="5ccde-115">Yazarak VsDevCmd.bat çalıştırın **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="5ccde-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="5ccde-116">VsDevCmd.bat bilgisayardan diğerine farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5ccde-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="5ccde-117">Eksik veya bozuk VsDevCmd.bat dosya başka bir bilgisayardan bir VsDevCmd.bat ile değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="5ccde-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="5ccde-118">Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ccde-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="5ccde-119">VsDevCmd.BAT için kullanılabilir seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5ccde-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="5ccde-120">VsDevCmd.BAT için kullanılabilir seçenekleri görmek için komutu çalıştırmak `-help` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="5ccde-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="5ccde-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ccde-121">See also</span></span>

- [<span data-ttu-id="5ccde-122">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="5ccde-122">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
