---
title: '&#39;Satır&#39; olan deyimleri artık desteklenmiyor (Visual Basic derleyici hatası)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 36226cc371ffb8a51cb8d0f918952f1c717aea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702988"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Satır&#39; olan deyimleri artık desteklenmiyor (Visual Basic derleyici hatası)
Satır deyimleri artık desteklenmiyor. Dosya g/ç işlevleri olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevlerini kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.  
  
 **Hata Kimliği:** BC30830  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic ile Dosya Erişimi](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
