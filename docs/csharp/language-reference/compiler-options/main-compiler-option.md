---
title: "-main (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a>/main (C# Derleyici Seçenekleri)
Birden fazla sınıf içeriyorsa bu seçenek, giriş içeren sınıf noktası programına belirtir bir **ana** yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 İçeren tür **ana** yöntemi.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla türü ile derlemeniz içeriyorsa, bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi, hangi türünü içeren belirtebilirsiniz **ana** programa giriş noktası olarak kullanmak istediğiniz yöntemi.  
  
 Bu seçenek, bir .exe dosyası derlerken kullanımı içindir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **Başlangıç nesnesi** özelliği.  
  
     Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve `t3.cs`, belirtme, **ana** yöntemi bulunan `Test2`:  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
