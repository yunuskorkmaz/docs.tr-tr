---
title: "Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
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
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama

VsDevCmd.bat dosyanın komut satırı derlemeleri etkinleştirmek için uygun ortam değişkenlerini ayarlar. VsDevCmd.bat hakkında daha fazla bilgi için bkz: [Bilgi Bankası makalesi Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).  

> [!NOTE]
> Visual Studio 2017 ile sunulan yeni bir dosya VsDevCmd.bat dosyasıdır. Visual Studio 2015 ve önceki sürümleri VSVARS32.bat aynı amaçla kullanılan. Bu dosyayı Visual Studio \Program Files\Microsoft depolanan\\*sürüm*\Common7\Tools veya Program dosyaları (x86) \Microsoft Visual Studio\\*sürüm*\Common7\Tools.
  
Visual Studio'nun geçerli sürümü Visual Studio'nun önceki bir sürümünü de olan bir bilgisayara yüklediyseniz, VsDevCmd.bat ve VSVARS32 çalıştırmamanız gerekir. Aynı komut istemi penceresinde farklı sürümlerdeki BAT. Bunun yerine, kendi penceresinde her sürüm için komutu çalıştırmanız gerekir.
  
### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT çalıştırmak için  
  
1.  Gelen **Başlat** menüsünde, açık **VS 2017 için geliştirici komut istemi**.  İçinde **Visual Studio 2017** klasör.
  
2.  Değiştirme \Program Visual Studio\\*sürüm*\\*sunumu*\Common7\Tools veya \Program dosyaları (x86) \Microsoft Visual Studio\\ *Sürüm*\\*sunumu*\Common7\Tools alt yüklemenizin.  (*Sürüm* olan *2017* geçerli sürümü için. *Teklifi* biri *Kurumsal*, *Professional* veya *topluluk*.)
  
3.  VsDevCmd.bat yazarak çalıştırırsınız **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat bilgisayardan diğerine farklılık gösterebilir. Eksik veya zarar görmüş VsDevCmd.bat dosya başka bir bilgisayardan VsDevCmd.bat ile değiştirmeyin. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı csc.exe derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
