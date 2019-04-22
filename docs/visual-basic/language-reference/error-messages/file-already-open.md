---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770366"
---
# <a name="file-already-open"></a><span data-ttu-id="9f949-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="9f949-102">File already open</span></span>
<span data-ttu-id="9f949-103">Bazen bir dosyayı başka önce kapatılması gereken `FileOpen` veya başka bir işlem ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="9f949-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="9f949-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="9f949-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="9f949-105">Bir sıralı çıkış modu `FileOpen` işlemi zaten açık olan bir dosya için yürütüldü</span><span class="sxs-lookup"><span data-stu-id="9f949-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="9f949-106">Bir deyimi açık bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="9f949-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f949-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9f949-107">To correct this error</span></span>  
  
1. <span data-ttu-id="9f949-108">Deyim yürütülmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="9f949-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f949-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f949-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
