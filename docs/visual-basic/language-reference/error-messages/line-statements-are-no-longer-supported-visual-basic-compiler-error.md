---
title: '&#39;Satır&#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Satır&#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)
Satır deyimleri artık desteklenmiyor. Dosya g/ç işlevselliği kullanılabilir olarak `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevselliği kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.  
  
 **Hata Kimliği:** BC30830  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Visual Basic ile Dosya Erişimi](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
