---
title: Dosya sonunun ötesinde giriş
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873959"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="1627d-102">Dosya sonunun ötesinde giriş</span><span class="sxs-lookup"><span data-stu-id="1627d-102">Input past end of file</span></span>

<span data-ttu-id="1627d-103">Bir `Input` ifade, boş olan bir dosyadan veya tüm verilerin kullanıldığı bir dosyadan okunuyor ya da `EOF` işlevi ikili erişim için açılmış bir dosya ile kullandınız.</span><span class="sxs-lookup"><span data-stu-id="1627d-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1627d-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1627d-104">To correct this error</span></span>  
  
1. <span data-ttu-id="1627d-105">`EOF` `Input` Dosya sonunu algılamak için deyimden hemen önce işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1627d-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="1627d-106">Dosya ikili erişim için açılırsa, `Seek` ve kullanın `Loc` .</span><span class="sxs-lookup"><span data-stu-id="1627d-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1627d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1627d-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
