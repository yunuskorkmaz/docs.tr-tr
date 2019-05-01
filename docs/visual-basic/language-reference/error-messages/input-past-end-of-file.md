---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 5da14c7a28ecdcd023fc6439cb6ed64444c1183b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013796"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="fa803-102">Dosya sonunun ötesinde giriş</span><span class="sxs-lookup"><span data-stu-id="fa803-102">Input past end of file</span></span>
<span data-ttu-id="fa803-103">Ya da bir `Input` ifadesi boş olan bir dosyayı veya tüm veriler kullanılır veya kullandığınız okuma `EOF` işlevi bir dosyayla ikili erişimi için açılır.</span><span class="sxs-lookup"><span data-stu-id="fa803-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa803-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fa803-104">To correct this error</span></span>  
  
1. <span data-ttu-id="fa803-105">Kullanım `EOF` hemen önce işlev `Input` deyimini dosyanın sonuna algılayın.</span><span class="sxs-lookup"><span data-stu-id="fa803-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="fa803-106">Dosya ikili erişimi için açılıp açılmadığını kullanın `Seek` ve `Loc`.</span><span class="sxs-lookup"><span data-stu-id="fa803-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa803-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa803-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
