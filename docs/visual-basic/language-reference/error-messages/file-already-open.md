---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586676"
---
# <a name="file-already-open"></a><span data-ttu-id="7e763-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="7e763-102">File already open</span></span>
<span data-ttu-id="7e763-103">Bazen bir dosya başka önce kapatılması gerekir `FileOpen` veya başka bir işlem oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7e763-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="7e763-104">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7e763-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="7e763-105">Sıralı çıkış modu `FileOpen` işlemi için zaten açık olan bir dosya yürütüldü</span><span class="sxs-lookup"><span data-stu-id="7e763-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="7e763-106">Bir deyim açık olan bir dosyaya başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="7e763-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e763-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7e763-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="7e763-108">Deyimini yürütmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="7e763-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e763-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e763-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
