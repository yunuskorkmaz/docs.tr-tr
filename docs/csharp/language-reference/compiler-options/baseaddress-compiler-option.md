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
ms.openlocfilehash: 3759067731902ba4f460ff850fb5e81f2e544e99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215238"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (C# Derleyici Seçenekleri)
**- Baseaddress** seçeneğini tercih edilen temel adrese DLL yükleneceği belirtmenize olanak sağlar. Bu seçeneği kullanmak neden ve ne zaman hakkında daha fazla bilgi için bkz: [Larry Osterman'ın blog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Arguments  
 `address`  
 DLL için temel adres. Bu adresi bir ondalık, onaltılık veya sekizlik sayı olarak belirtilebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir DLL için varsayılan taban adresi .NET Framework ortak dil çalışma zamanı tarafından ayarlanır.  
  
 Bu adres alt sıra Word'de yuvarlanacağı unutmayın. Örneğin, 0x11110001 belirtirseniz, 0x11110000 için yuvarlanır.  
  
 Bir DLL için imzalama işlemini tamamlamak için SN kullanın. EXE -R seçeneğiyle.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Tıklatın **Gelişmiş** düğmesi.  
  
4.  Değiştirme **DLL ana adresi** özelliği.  
  
     Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
