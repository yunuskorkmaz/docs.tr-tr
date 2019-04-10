---
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339079"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)
Satır deyimleri artık desteklenmiyor. Dosya g/ç işlevleri olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevlerini kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.  
  
 **Hata Kimliği:** BC30830  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2. Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic ile Dosya Erişimi](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
