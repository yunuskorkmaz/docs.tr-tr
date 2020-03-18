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
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Visual Studio Komut Satırı için ortam değişkenlerini ayarlama

VsDevCmd.bat dosyası komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.

> [!NOTE]
> Visual Studio 2015 ve önceki sürümlerde vsdevcmd.bat değil, aynı amaç için VSVARS32.bat kullanılmıştır. Bu dosya \Program Files\Microsoft Visual\\Studio*Version*\Common7\Tools veya Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools'ta depolandı.

Visual Studio'nun geçerli sürümü Visual Studio'nun daha önceki bir sürümüne sahip bir bilgisayara yüklenmişse, VsDevCmd.bat ve VSVARS32'yi çalıştırmamalısınız. Aynı Komut İstem penceresinde farklı sürümlerden BAT. Bunun yerine, her sürüm için komutu kendi penceresinde çalıştırmanız gerekir.

### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT çalıştırmak için

1. **Başlat** menüsünden VS **2019 için Geliştirici Komut Komut Ustem'ini**açın.  **Visual Studio 2019** klasöründe.

2. \Program Files\Microsoft Visual Studio\\*Sürüm*\\*Sunusu*\\\Common7\Tools veya \Program Files (x86)\Microsoft Visual Studio*Sürüm*\\*Sunan*\Common7\Tools alt dizini yüklemenizi değiştirin.  (*Sürüm* geçerli sürüm için *2019'dur.* *Sunan* *kurumsal*biridir , *Profesyonel* veya *Topluluk*.)

3. **VsDevCmd yazarak VsDevCmd.bat**çalıştırın.

    > [!CAUTION]
    > VsDevCmd.bat bilgisayardan bilgisayara değişebilir. Eksik veya hasarlı Bir VsDevCmd.bat dosyalarını başka bir bilgisayardan bir VsDevCmd.bat ile değiştirmeyin. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.

### <a name="available-options-for-vsdevcmdbat"></a>VsDevCmd.BAT için kullanılabilir seçenekler

VsDevCmd.BAT için kullanılabilir seçenekleri görmek için komutu seçeneğiyle çalıştırın: `-help`

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](./command-line-building-with-csc-exe.md)
