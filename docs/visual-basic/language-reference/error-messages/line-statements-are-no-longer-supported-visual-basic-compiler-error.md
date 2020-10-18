---
title: "'Line' deyimleri artık desteklenmiyor (Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: f34095becf321c6cb4b316b6378a2da0107577ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162485"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="a2ebc-102">BC30830: ' Line ' deyimleri artık desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="a2ebc-102">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="a2ebc-103">Line deyimleri artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="a2ebc-103">Line statements are no longer supported.</span></span> <span data-ttu-id="a2ebc-104">Dosya g/ç işlevselliği olarak kullanılabilir `Microsoft.VisualBasic.FileSystem.LineInput` ve grafik işlevleri olarak kullanılabilir `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="a2ebc-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="a2ebc-105">**Hata kimliği:** BC30830</span><span class="sxs-lookup"><span data-stu-id="a2ebc-105">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a2ebc-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a2ebc-106">To correct this error</span></span>

- <span data-ttu-id="a2ebc-107">Dosya erişimi gerçekleştiriyorsanız kullanın `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="a2ebc-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="a2ebc-108">Grafik uyguluyorsanız, kullanın `System.Drawing.Graphics.Drawline` .</span><span class="sxs-lookup"><span data-stu-id="a2ebc-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2ebc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ebc-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="a2ebc-110">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="a2ebc-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
