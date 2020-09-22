---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874169"
---
# <a name="file-already-open"></a><span data-ttu-id="f8526-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="f8526-102">File already open</span></span>

<span data-ttu-id="f8526-103">Bazen bir dosyanın başka bir `FileOpen` işlemin gerçekleşebilmesi için kapatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8526-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="f8526-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="f8526-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="f8526-105">`FileOpen`Zaten açık olan bir dosya için sıralı çıkış modu işlemi yürütüldü</span><span class="sxs-lookup"><span data-stu-id="f8526-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="f8526-106">Bir ifade açık bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="f8526-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8526-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f8526-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f8526-108">İfadeyi yürütmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="f8526-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8526-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8526-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
