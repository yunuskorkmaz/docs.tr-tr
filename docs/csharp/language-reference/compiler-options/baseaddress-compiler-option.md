---
title: -baseaddress (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f138f445b8a335c7505e25b34f560c4da40ab2dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937206"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (C# Derleyici Seçenekleri)
**-baseaddress** seçeneği, DLL yüklemek için tercih edilen temel adresi belirtmenizi sağlar. Bu seçeneğin ne zaman ve neden kullanılacağı hakkında daha fazla bilgi için [Larry Osterman'ın WebGünlüğü'ne](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)bakın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `address`  
 DLL'nin temel adresi. Bu adres ondalık, hexadecimal veya oksal sayı olarak belirtilebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma süresi tarafından ayarlanır.  
  
 Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın. Örneğin, 0x111100001 belirtirseniz, 0x11110000 yuvarlatılır.  
  
 Bir DLL için imzalama işlemini tamamlamak için SN kullanın. -R seçeneği ile EXE.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. **Gelişmiş** düğmesini tıklatın.  
  
4. **DLL Temel Adres** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>ayarlamak için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
