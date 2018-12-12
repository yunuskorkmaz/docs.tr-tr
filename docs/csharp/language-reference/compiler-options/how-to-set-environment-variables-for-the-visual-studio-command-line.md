---
title: 'Nasıl Yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama'
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
ms.openlocfilehash: 3563f668dfd4610e1c5cd7d7f8633943c654f193
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286448"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Nasıl Yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama

VsDevCmd.bat dosya komut satırı derlemeleri etkinleştirmek için uygun ortam değişkenlerini ayarlar.

> [!NOTE]
> Visual Studio 2017 ile sunulan yeni bir dosya VsDevCmd.bat dosyasıdır. Visual Studio 2015 ve önceki sürümleri VSVARS32.bat aynı amaçla kullanılan. Bu dosya, \Program Files\Microsoft Visual Studio depolanmış\\*sürüm*\Common7\Tools veya Program dosyaları (x86) \Microsoft Visual Studio\\*sürüm*\Common7\Tools.
  
Visual Studio'nun geçerli sürümü Visual Studio'nun önceki bir sürümü olan bir bilgisayarda yüklü ise, VsDevCmd.bat ve VSVARS32 çalıştırmamanız gerekir. Aynı komut istemi penceresinde farklı sürümlerine ait BAT. Bunun yerine, kendi penceresinde her sürüm için komutu çalıştırmanız gerekir.
  
### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT çalıştırmak için  
  
1.  Gelen **Başlat** menüsünde, açık **VS 2017 için geliştirici komut istemi**.  İçinde **Visual Studio 2017** klasör.
  
2.  Değiştirme \Program Visual Studio'ya\\*sürüm*\\*sunan*\Common7\Tools veya \Program dosyaları (x86) \Microsoft Visual Studio\\ *Sürüm*\\*sunan*yüklemenizin \Common7\Tools alt dizinine geçin.  (*Sürüm* olduğu *2017* geçerli sürümü için. *Teklif* biri *Kurumsal*, *Professional* veya *topluluk*.)
  
3.  Yazarak VsDevCmd.bat çalıştırın **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat bilgisayardan diğerine farklılık gösterebilir. Eksik veya bozuk VsDevCmd.bat dosya başka bir bilgisayardan bir VsDevCmd.bat ile değiştirmeyin. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.  

### <a name="available-options-for-vsdevcmdbat"></a>VsDevCmd.BAT için kullanılabilir seçenekleri

VsDevCmd.BAT için kullanılabilir seçenekleri görmek için komutu çalıştırmak `-help` seçeneği:
```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Ayrıca Bkz.  

- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
