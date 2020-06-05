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
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="e40a0-102">'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)</span><span class="sxs-lookup"><span data-stu-id="e40a0-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="e40a0-103">Line deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e40a0-103">Line statements are no longer supported.</span></span> <span data-ttu-id="e40a0-104">Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="e40a0-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="e40a0-105">**Hata kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="e40a0-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e40a0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e40a0-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e40a0-107">Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="e40a0-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="e40a0-108">Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .</span><span class="sxs-lookup"><span data-stu-id="e40a0-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40a0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e40a0-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="e40a0-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="e40a0-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
