---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: e565dbd6352a8f76290f3f58d62e2e14a18ef45f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823512"
---
# <a name="file-already-open"></a><span data-ttu-id="53dfa-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="53dfa-102">File already open</span></span>
<span data-ttu-id="53dfa-103">Bazen bir dosyayı başka önce kapatılması gereken `FileOpen` veya başka bir işlem ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="53dfa-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="53dfa-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="53dfa-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="53dfa-105">Bir sıralı çıkış modu `FileOpen` işlemi zaten açık olan bir dosya için yürütüldü</span><span class="sxs-lookup"><span data-stu-id="53dfa-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="53dfa-106">Bir deyimi açık bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="53dfa-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53dfa-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="53dfa-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="53dfa-108">Deyim yürütülmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="53dfa-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53dfa-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53dfa-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
