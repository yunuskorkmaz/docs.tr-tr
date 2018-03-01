---
title: "DLL yüklenirken hata (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="928ed-102">DLL yüklenirken hata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="928ed-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="928ed-103">Dinamik bağlantı kitaplığı (DLL) içinde belirtilen bir kitaplıktır `Lib` yan tümcesinde bir `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="928ed-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="928ed-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="928ed-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="928ed-105">Dosya DLL yürütülebilir değil.</span><span class="sxs-lookup"><span data-stu-id="928ed-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="928ed-106">Dosya bir Microsoft Windows dll dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="928ed-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="928ed-107">DLL mevcut değil başka bir DLL başvurur.</span><span class="sxs-lookup"><span data-stu-id="928ed-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="928ed-108">DLL veya başvurulan DLL yolunda belirtilen bir dizin değil.</span><span class="sxs-lookup"><span data-stu-id="928ed-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="928ed-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="928ed-109">To correct this error</span></span>  
  
-   <span data-ttu-id="928ed-110">Dosya bir kaynak metin dosyası ve bu nedenle değil DLL yürütülebilir ise derlenmiş ve gerekir DLL yürütülebilir dosya biçimine bağlı.</span><span class="sxs-lookup"><span data-stu-id="928ed-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="928ed-111">Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğer edinin.</span><span class="sxs-lookup"><span data-stu-id="928ed-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="928ed-112">DLL mevcut değil başka bir DLL başvuruyorsa, başvurulan DLL edinmek ve kullanılabilir yapın.</span><span class="sxs-lookup"><span data-stu-id="928ed-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="928ed-113">DLL veya başvurulan DLL yolu tarafından belirtilen bir dizinde değilse, DLL başvurulan bir dizinine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="928ed-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="928ed-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="928ed-114">See Also</span></span>  
 [<span data-ttu-id="928ed-115">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="928ed-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
