---
title: "&#39; Çizgi &#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39; Çizgi &#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)
Satır deyimleri artık desteklenmiyor. Dosya g/ç işlevselliği kullanılabilir olarak `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevselliği kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.  
  
 **Hata Kimliği:** BC30830  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Visual Basic ile dosya erişimi](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
