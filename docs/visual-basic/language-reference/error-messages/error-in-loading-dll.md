---
title: DLL yüklenirken hata (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 76a0a443fd9f8a6dec5ead24bc75c97d89d6c36b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518468"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="64fe3-102">DLL yüklenirken hata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64fe3-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="64fe3-103">Bir dinamik bağlantı kitaplığı (DLL) belirtilen bir kitaplıktır `Lib` yan tümcesi bir `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="64fe3-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="64fe3-104">Bu hata için olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="64fe3-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="64fe3-105">DLL yürütülebilir dosya değil.</span><span class="sxs-lookup"><span data-stu-id="64fe3-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="64fe3-106">Dosya, Microsoft Windows DLL değil.</span><span class="sxs-lookup"><span data-stu-id="64fe3-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="64fe3-107">DLL mevcut değilse başka bir DLL başvurusu.</span><span class="sxs-lookup"><span data-stu-id="64fe3-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="64fe3-108">DLL veya başvurulan DLL belirtilen yolda bir dizin değil.</span><span class="sxs-lookup"><span data-stu-id="64fe3-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="64fe3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="64fe3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="64fe3-110">Dosya bir kaynak metin dosyası ve bu nedenle DLL çalıştırılabilir değil ise, derlenmiş ve gerekir DLL yürütülebilir dosya biçimine bağlı.</span><span class="sxs-lookup"><span data-stu-id="64fe3-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="64fe3-111">Microsoft Windows DLL dosyası değil, eşdeğer Microsoft Windows edinin.</span><span class="sxs-lookup"><span data-stu-id="64fe3-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="64fe3-112">DLL mevcut değilse başka bir DLL başvuruyorsa, başvurulan DLL edinin ve kullanılabilir hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="64fe3-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="64fe3-113">DLL veya başvurulan DLL yolu tarafından belirtilen bir dizinde değilse DLL başvurulan bir dizinine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="64fe3-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fe3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64fe3-114">See also</span></span>
- [<span data-ttu-id="64fe3-115">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="64fe3-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
