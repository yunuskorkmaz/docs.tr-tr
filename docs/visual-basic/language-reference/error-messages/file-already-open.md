---
description: 'Daha fazla bilgi edinin: dosya zaten açık'
title: Dosya zaten açık
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 2f3345c15f4a3095a8e733c2c8424edb25b4dee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796307"
---
# <a name="file-already-open"></a><span data-ttu-id="23e52-103">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="23e52-103">File already open</span></span>

<span data-ttu-id="23e52-104">Bazen bir dosyanın başka bir `FileOpen` işlemin gerçekleşebilmesi için kapatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23e52-104">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="23e52-105">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="23e52-105">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="23e52-106">`FileOpen`Zaten açık olan bir dosya için sıralı çıkış modu işlemi yürütüldü</span><span class="sxs-lookup"><span data-stu-id="23e52-106">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="23e52-107">Bir ifade açık bir dosyaya başvurur.</span><span class="sxs-lookup"><span data-stu-id="23e52-107">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="23e52-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="23e52-108">To correct this error</span></span>

- <span data-ttu-id="23e52-109">İfadeyi yürütmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="23e52-109">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="23e52-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23e52-110">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
