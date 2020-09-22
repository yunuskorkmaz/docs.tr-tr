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
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="edb12-102">'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)</span><span class="sxs-lookup"><span data-stu-id="edb12-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>

<span data-ttu-id="edb12-103">Line deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="edb12-103">Line statements are no longer supported.</span></span> <span data-ttu-id="edb12-104">Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="edb12-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="edb12-105">**Hata kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="edb12-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="edb12-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="edb12-106">To correct this error</span></span>  
  
1. <span data-ttu-id="edb12-107">Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="edb12-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="edb12-108">Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .</span><span class="sxs-lookup"><span data-stu-id="edb12-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb12-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb12-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="edb12-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="edb12-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
