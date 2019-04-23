---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768559"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="224d0-102">Dosya sonunun ötesinde giriş</span><span class="sxs-lookup"><span data-stu-id="224d0-102">Input past end of file</span></span>
<span data-ttu-id="224d0-103">Ya da bir `Input` ifadesi boş olan bir dosyayı veya tüm veriler kullanılır veya kullandığınız okuma `EOF` işlevi bir dosyayla ikili erişimi için açılır.</span><span class="sxs-lookup"><span data-stu-id="224d0-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="224d0-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="224d0-104">To correct this error</span></span>  
  
1. <span data-ttu-id="224d0-105">Kullanım `EOF` hemen önce işlev `Input` deyimini dosyanın sonuna algılayın.</span><span class="sxs-lookup"><span data-stu-id="224d0-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="224d0-106">Dosya ikili erişimi için açılıp açılmadığını kullanın `Seek` ve `Loc`.</span><span class="sxs-lookup"><span data-stu-id="224d0-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="224d0-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="224d0-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
