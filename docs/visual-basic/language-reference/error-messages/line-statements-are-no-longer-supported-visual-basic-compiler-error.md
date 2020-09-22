---
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 4ca1538dbde0d585b7b421d60cde4531c00e9145
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873838"
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
