---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d98a9f3cadc42021c302915cfc5b058b41e11ec6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="out-visual-basic"></a>/out (Visual Basic)
Çıktı dosyası adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gerekli. Derleyici çıktı dosyası adını oluşturur. Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").|  
  
## <a name="remarks"></a>Açıklamalar  
 Tam adı ve uzantısı oluşturmak için dosya belirtin. Bunu yapmazsanız, .exe dosya gelen kaynak kodu içeren dosyanın adını alır `Sub Main` yordamı ve .dll dosyasının ilk kaynak kod dosyasının adını alır.  
  
 Bir .exe veya .dll uzantısı olmadan dosya adı belirtirseniz, derleyici uzantısını otomatik sizin için belirtilen değer bağlı olarak ekler `/target` derleyici seçeneği.  
  
|Visual Studio tümleşik geliştirme ortamında out ayarlamak için|  
|---|  
|1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Tıklatın **uygulama** sekmesi.<br />3.  Değer değiştirme **derleme adı** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve çıktı dosyası oluşturur `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
