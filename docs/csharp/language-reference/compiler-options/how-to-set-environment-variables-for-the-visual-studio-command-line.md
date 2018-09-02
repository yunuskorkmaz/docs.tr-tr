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
ms.openlocfilehash: 77375e428fe0563c0b533ca97abd21070e850682
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466744"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama

VsDevCmd.bat dosya komut satırı derlemeleri etkinleştirmek için uygun ortam değişkenlerini ayarlar. VsDevCmd.bat hakkında daha fazla bilgi için bkz: [Bilgi Bankası makalesi Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> Visual Studio 2017 ile sunulan yeni bir dosya VsDevCmd.bat dosyasıdır. Visual Studio 2015 ve önceki sürümleri VSVARS32.bat aynı amaçla kullanılan. Bu dosya, \Program Files\Microsoft Visual Studio depolanmış\\*sürüm*\Common7\Tools veya Program dosyaları (x86) \Microsoft Visual Studio\\*sürüm*\Common7\Tools.
  
Visual Studio'nun geçerli sürümü Visual Studio'nun önceki bir sürümü olan bir bilgisayarda yüklü ise, VsDevCmd.bat ve VSVARS32 çalıştırmamanız gerekir. Aynı komut istemi penceresinde farklı sürümlerine ait BAT. Bunun yerine, kendi penceresinde her sürüm için komutu çalıştırmanız gerekir.
  
### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT çalıştırmak için  
  
1.  Gelen **Başlat** menüsünde, açık **VS 2017 için geliştirici komut istemi**.  İçinde **Visual Studio 2017** klasör.
  
2.  Değiştirme \Program Visual Studio'ya\\*sürüm*\\*sunan*\Common7\Tools veya \Program dosyaları (x86) \Microsoft Visual Studio\\ *Sürüm*\\*sunan*yüklemenizin \Common7\Tools alt dizinine geçin.  (*Sürüm* olduğu *2017* geçerli sürümü için. *Teklif* biri *Kurumsal*, *Professional* veya *topluluk*.)
  
3.  Yazarak VsDevCmd.bat çalıştırın **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat bilgisayardan diğerine farklılık gösterebilir. Eksik veya bozuk VsDevCmd.bat dosya başka bir bilgisayardan bir VsDevCmd.bat ile değiştirmeyin. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
