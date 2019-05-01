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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921075"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="30ac8-102">'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)</span><span class="sxs-lookup"><span data-stu-id="30ac8-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="30ac8-103">Satır deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="30ac8-103">Line statements are no longer supported.</span></span> <span data-ttu-id="30ac8-104">Dosya g/ç işlevleri olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevlerini kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="30ac8-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="30ac8-105">**Hata Kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="30ac8-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="30ac8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="30ac8-106">To correct this error</span></span>  
  
1. <span data-ttu-id="30ac8-107">Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="30ac8-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="30ac8-108">Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="30ac8-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ac8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30ac8-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="30ac8-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="30ac8-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
