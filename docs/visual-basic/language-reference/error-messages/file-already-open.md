---
title: "Dosya zaten açık"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="d5767-102">Dosya zaten açık</span><span class="sxs-lookup"><span data-stu-id="d5767-102">File already open</span></span>
<span data-ttu-id="d5767-103">Bazen bir dosya başka önce kapatılması gerekir `FileOpen` veya başka bir işlem oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="d5767-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="d5767-104">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5767-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="d5767-105">Sıralı çıkış modu `FileOpen` işlemi için zaten açık olan bir dosya yürütüldü</span><span class="sxs-lookup"><span data-stu-id="d5767-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="d5767-106">Bir deyim açık olan bir dosyaya başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="d5767-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5767-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d5767-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="d5767-108">Deyimini yürütmeden önce dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="d5767-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5767-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5767-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
