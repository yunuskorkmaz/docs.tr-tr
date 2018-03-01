---
title: "&#39; Çizgi &#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="4dec8-102">&#39; Çizgi &#39; deyimleri olan artık desteklenen (Visual Basic derleyici hatası)</span><span class="sxs-lookup"><span data-stu-id="4dec8-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="4dec8-103">Satır deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4dec8-103">Line statements are no longer supported.</span></span> <span data-ttu-id="4dec8-104">Dosya g/ç işlevselliği kullanılabilir olarak `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevselliği kullanılabilir olarak `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="4dec8-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="4dec8-105">**Hata Kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="4dec8-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4dec8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4dec8-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4dec8-107">Dosya erişimi gerçekleştirme kullanırsanız `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="4dec8-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="4dec8-108">Grafik gerçekleştirme kullanırsanız `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="4dec8-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dec8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4dec8-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="4dec8-110">Visual Basic ile dosya erişimi</span><span class="sxs-lookup"><span data-stu-id="4dec8-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
