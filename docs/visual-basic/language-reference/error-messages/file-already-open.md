---
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162758"
---
# <a name="file-already-open"></a><span data-ttu-id="87831-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="87831-102">File already open</span></span>

<span data-ttu-id="87831-103">Bazen bir dosyanın başka bir `FileOpen` işlemin gerçekleşebilmesi için kapatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87831-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="87831-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="87831-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="87831-105">`FileOpen`Zaten açık olan bir dosya için sıralı çıkış modu işlemi yürütüldü</span><span class="sxs-lookup"><span data-stu-id="87831-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="87831-106">Bir ifade açık bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="87831-106">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="87831-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="87831-107">To correct this error</span></span>

- <span data-ttu-id="87831-108">İfadeyi yürütmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="87831-108">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="87831-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87831-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
