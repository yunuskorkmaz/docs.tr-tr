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
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="69c94-103">BC30830: ' Line ' deyimleri artık desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="69c94-103">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="69c94-104">Line deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="69c94-104">Line statements are no longer supported.</span></span> <span data-ttu-id="69c94-105">Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="69c94-105">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="69c94-106">**Hata kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="69c94-106">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="69c94-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="69c94-107">To correct this error</span></span>

- <span data-ttu-id="69c94-108">Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="69c94-108">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="69c94-109">Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .</span><span class="sxs-lookup"><span data-stu-id="69c94-109">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="69c94-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69c94-110">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="69c94-111">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="69c94-111">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
