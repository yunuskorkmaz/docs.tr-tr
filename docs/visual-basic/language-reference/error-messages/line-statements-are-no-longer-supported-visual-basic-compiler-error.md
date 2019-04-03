---
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 7616bcdc39ab479049586534fac22f1e2d96a700
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831845"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="35804-102">'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)</span><span class="sxs-lookup"><span data-stu-id="35804-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="35804-103">Satır deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="35804-103">Line statements are no longer supported.</span></span> <span data-ttu-id="35804-104">Dosya g/ç işlevleri olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevlerini kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="35804-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="35804-105">**Hata Kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="35804-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35804-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="35804-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="35804-107">Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="35804-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="35804-108">Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="35804-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35804-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35804-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="35804-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="35804-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
