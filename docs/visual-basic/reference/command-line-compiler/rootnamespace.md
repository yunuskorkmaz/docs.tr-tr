---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a>/rootnamespace
Tüm tür bildirimleri için bir ad alanını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`namespace`|Geçerli projenin tüm tür bildirimleri kapsamak ad alanı adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio yürütülebilir dosya (Devenv.exe) oluşturulmuş bir projeyi derlemek için Visual Studio tümleşik geliştirme ortamında kullanım kullanırsanız `/rootnamespace` değerini belirtmek için <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> özelliği. Bkz: [Devenv komut satırı anahtarları](/visualstudio/ide/reference/devenv-command-line-switches) daha fazla bilgi için.  
  
 Ortak dil çalışma zamanı MSIL ayrıştırıcı kullanın (`Ildasm.exe`) çıkış dosyanızın ad alanı adlarını görüntülemek için.  
  
|Tümleşik geliştirme ortamı/RootNamespace Visual Studio'da ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **uygulama** sekmesi.<br />3.  Değer değiştirme **kök Namespace** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `In.vb` ve ad alanındaki tüm tür bildirimleri barındırır `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL Ayrıştırıcı)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
