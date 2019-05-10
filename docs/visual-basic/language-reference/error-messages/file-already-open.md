---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 8ec878e04b0128c997c5be51d2c714d55abcde8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665114"
---
# <a name="file-already-open"></a><span data-ttu-id="d74cc-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="d74cc-102">File already open</span></span>
<span data-ttu-id="d74cc-103">Bazen bir dosyayı başka önce kapatılması gereken `FileOpen` veya başka bir işlem ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="d74cc-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="d74cc-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="d74cc-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="d74cc-105">Bir sıralı çıkış modu `FileOpen` işlemi zaten açık olan bir dosya için yürütüldü</span><span class="sxs-lookup"><span data-stu-id="d74cc-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="d74cc-106">Bir deyimi açık bir dosyaya.</span><span class="sxs-lookup"><span data-stu-id="d74cc-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d74cc-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d74cc-107">To correct this error</span></span>  
  
1. <span data-ttu-id="d74cc-108">Deyim yürütülmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="d74cc-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74cc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d74cc-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
