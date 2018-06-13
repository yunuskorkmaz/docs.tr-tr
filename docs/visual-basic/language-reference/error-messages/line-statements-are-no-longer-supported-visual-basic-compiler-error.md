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
ms.locfileid: "33587885"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="4049f-102">&#39;Satır&#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)</span><span class="sxs-lookup"><span data-stu-id="4049f-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="4049f-103">Satır deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4049f-103">Line statements are no longer supported.</span></span> <span data-ttu-id="4049f-104">Dosya g/ç işlevselliği kullanılabilir olarak `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevselliği kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="4049f-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="4049f-105">**Hata Kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="4049f-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4049f-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4049f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4049f-107">Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="4049f-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="4049f-108">Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="4049f-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4049f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4049f-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="4049f-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="4049f-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
