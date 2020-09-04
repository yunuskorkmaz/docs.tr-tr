---
description: -BaseAddress (C# derleyici seçenekleri)
title: -BaseAddress (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: f79ee449eafd04906dab49700a1af6441d54cece
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464889"
---
# <a name="-baseaddress-c-compiler-options"></a>-BaseAddress (C# derleyici seçenekleri)
**-BaseAddress** SEÇENEĞI, dll 'nin yükleneceği tercih edilen temel adresi belirtmenizi sağlar. Bu seçeneğin ne zaman ve neden kullanıldığı hakkında daha fazla bilgi için bkz. [Larry Osterman 'ın Web günlüğü](https://docs.microsoft.com/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `address`  
 DLL 'nin temel adresi. Bu adres ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir DLL için varsayılan temel adres, .NET ortak dil çalışma zamanı tarafından ayarlanır.  
  
 Bu adresteki alt sıra sözcüğünün yuvarlanacağını unutmayın. Örneğin, 0x11110001 belirtirseniz, 0x11110000 ' ya yuvarlanır.  
  
 DLL imzalama işlemini gerçekleştirmek için,-R seçeneğiyle SN.EXE kullanın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Gelişmiş** düğmesine tıklayın.  
  
4. **Dll taban adresi** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
