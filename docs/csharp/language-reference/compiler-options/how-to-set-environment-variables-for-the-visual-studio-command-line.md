---
description: Visual Studio Komut Satırı için ortam değişkenlerini ayarlama
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
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125611"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Visual Studio Komut Satırı için ortam değişkenlerini ayarlama

VsDevCmd.bat dosyası, komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.

> [!NOTE]
> Visual Studio 2015 ve önceki sürümleri, aynı amaçla VsDevCmd.bat değil VSVARS32.bat kullandı. Bu dosya \Program Files\Microsoft Visual Studio \\ *Version*\Common7\Tools veya Program Files (x86) \Microsoft Visual Studio \\ *Version*\Common7\Tools. içinde depolandı

Visual Studio 'nun geçerli sürümü, Visual Studio 'nun önceki bir sürümüne de sahip olan bir bilgisayarda yüklüyse, aynı komut Istemi penceresinde farklı sürümlerden VsDevCmd.bat ve VSVARS32.BAT çalıştırmamalıdır. Bunun yerine, her sürüm için komutunu kendi penceresinde çalıştırmalısınız.

### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT çalıştırmak için

1. **Başlangıç** menüsünde **VS 2019 için geliştirici komut istemi**açın.  **Visual Studio 2019** klasöründedir.

2. \\*Version* \\ *Offering*Yüklemenizin \Common7\Tools veya \Program Files (x86) \Microsoft Visual Studio \\ *Version* \\ *teklif*\Common7\Tools alt dizinine yönelik \Program Files\Microsoft Visual Studio Version teklifini değiştirin.  (*Sürüm* , geçerli sürüm için *2019* . *Teklif* , *Enterprise*, *Professional* veya *Community*'den biridir.)

3. **Vsdevcmd**yazarak VsDevCmd.bat çalıştırın.

    > [!CAUTION]
    > VsDevCmd.bat bilgisayardan bilgisayara farklılık gösterebilir. Eksik veya hasarlı bir VsDevCmd.bat dosyasını başka bir bilgisayardaki VsDevCmd.bat değiştirme. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.

### <a name="available-options-for-vsdevcmdbat"></a>VsDevCmd.BAT için kullanılabilir seçenekler

VsDevCmd.BAT için kullanılabilir seçenekleri görmek için komutunu `-help` seçeneğiyle çalıştırın:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](./command-line-building-with-csc-exe.md)
