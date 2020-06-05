---
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397304"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)
Line deyimleri artık desteklenmiyor. Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .  
  
 **Hata kimliği:** BC30830  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .  
  
2. Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic ile Dosya Erişimi](../../developing-apps/programming/drives-directories-files/file-access.md)
