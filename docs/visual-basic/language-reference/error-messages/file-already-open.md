---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: cda72e03eb5c2469b8106957a0c50fbfa5314549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567041"
---
# <a name="file-already-open"></a><span data-ttu-id="b29d0-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="b29d0-102">File already open</span></span>
<span data-ttu-id="b29d0-103">Bazen bir dosyayı başka önce kapatılması gereken `FileOpen` veya başka bir işlem ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="b29d0-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="b29d0-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="b29d0-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="b29d0-105">Bir sıralı çıkış modu `FileOpen` işlemi zaten açık olan bir dosya için yürütüldü</span><span class="sxs-lookup"><span data-stu-id="b29d0-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="b29d0-106">Bir deyimi açık bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="b29d0-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b29d0-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b29d0-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="b29d0-108">Deyim yürütülmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b29d0-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29d0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b29d0-109">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
