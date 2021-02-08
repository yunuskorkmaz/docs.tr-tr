---
description: 'Daha fazla bilgi edinin: dosya sonunun ötesinde giriş'
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: b65a57bdc56367518a93880be28781e56c9b99cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796047"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="d9e50-103">Dosya sonunun ötesinde giriş</span><span class="sxs-lookup"><span data-stu-id="d9e50-103">Input past end of file</span></span>

<span data-ttu-id="d9e50-104">Bir `Input` ifade, boş olan bir dosyadan veya tüm verilerin kullanıldığı bir dosyadan okunuyor ya da `EOF` işlevi ikili erişim için açılmış bir dosya ile kullandınız.</span><span class="sxs-lookup"><span data-stu-id="d9e50-104">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9e50-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d9e50-105">To correct this error</span></span>  
  
1. <span data-ttu-id="d9e50-106">`EOF` `Input` Dosya sonunu algılamak için deyimden hemen önce işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9e50-106">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="d9e50-107">Dosya ikili erişim için açılırsa, `Seek` ve kullanın `Loc` .</span><span class="sxs-lookup"><span data-stu-id="d9e50-107">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e50-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9e50-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
