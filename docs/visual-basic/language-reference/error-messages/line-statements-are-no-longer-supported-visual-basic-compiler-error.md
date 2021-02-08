---
description: "Hakkında daha fazla bilgi edinin: BC30830: ' Line ' deyimleri artık desteklenmiyor"
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 16696856cee365171000e7b0abc206c42d3f3174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795878"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a>BC30830: ' Line ' deyimleri artık desteklenmiyor

Line deyimleri artık desteklenmiyor. Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .

 **Hata kimliği:** BC30830

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .

- Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic ile Dosya Erişimi](../../developing-apps/programming/drives-directories-files/file-access.md)
