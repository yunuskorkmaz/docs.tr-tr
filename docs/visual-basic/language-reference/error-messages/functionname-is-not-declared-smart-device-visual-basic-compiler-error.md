---
title: "'<functionname>' bildirilmedi (Akıllı Cihaz/Visual Basic Derleyici Hatası)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 5e0f6dd2da404ed988af15fadadd8ecd4a491189
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874060"
---
# <a name="functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="686b7-102">' \<functionname> ' bildirilmemiş (akıllı cihaz/Visual Basic derleyici hatası)</span><span class="sxs-lookup"><span data-stu-id="686b7-102">'\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="686b7-103"><`functionname`> bildirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="686b7-103"><`functionname`> is not declared.</span></span> <span data-ttu-id="686b7-104">Dosya g/ç işlevselliği normalde `Microsoft.VisualBasic` ad alanında kullanılabilir, ancak .NET Compact Framework hedeflenen sürümü bunu desteklemez.</span><span class="sxs-lookup"><span data-stu-id="686b7-104">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>  
  
 <span data-ttu-id="686b7-105">**Hata kimliği:** BC30766</span><span class="sxs-lookup"><span data-stu-id="686b7-105">**Error ID:** BC30766</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="686b7-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="686b7-106">To correct this error</span></span>  
  
- <span data-ttu-id="686b7-107">Ad alanında tanımlanan işlevlerle dosya işlemleri gerçekleştirin `System.IO` .</span><span class="sxs-lookup"><span data-stu-id="686b7-107">Perform file operations with functions defined in the `System.IO` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686b7-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="686b7-108">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="686b7-109">Visual Basic ile Dosya Erişimi</span><span class="sxs-lookup"><span data-stu-id="686b7-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
