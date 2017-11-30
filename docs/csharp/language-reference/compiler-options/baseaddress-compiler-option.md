---
title: "-baseaddress (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (C# Derleyici Seçenekleri)
**/Baseaddress** seçeneğini tercih edilen temel adrese DLL yükleneceği belirtmenize olanak sağlar. Bu seçeneği kullanmak neden ve ne zaman hakkında daha fazla bilgi için bkz: [Larry Osterman'ın blog](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/baseaddress:address  
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
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
