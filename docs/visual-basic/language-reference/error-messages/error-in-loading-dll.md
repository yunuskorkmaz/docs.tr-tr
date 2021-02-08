---
description: 'Hakkında daha fazla bilgi edinin: DLL yüklenirken hata (Visual Basic)'
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 098d05e93d328f3667000bd81290f4b77cf7949e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796515"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="d1a8a-103">DLL yüklenirken hata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1a8a-103">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="d1a8a-104">Dinamik bağlantı kitaplığı (DLL), `Lib` bir deyimin yan tümcesinde belirtilen bir kitaplıktır `Declare` .</span><span class="sxs-lookup"><span data-stu-id="d1a8a-104">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="d1a8a-105">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d1a8a-105">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="d1a8a-106">Dosya DLL yürütülebilir dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-106">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="d1a8a-107">Dosya bir Microsoft Windows DLL 'i değil.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-107">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="d1a8a-108">DLL, mevcut olmayan başka bir DLL 'ye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-108">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="d1a8a-109">DLL veya başvurulan DLL, yolda belirtilen bir dizin içinde değil.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-109">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1a8a-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d1a8a-110">To correct this error</span></span>  
  
- <span data-ttu-id="d1a8a-111">Dosya bir kaynak-metin dosyasıdır ve bu nedenle DLL yürütülebilir dosyası değilse, derlenmesi ve DLL yürütülebilir bir formla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-111">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="d1a8a-112">Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğerini edinin.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-112">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="d1a8a-113">DLL, mevcut olmayan başka bir DLL 'ye başvuruyorsa, başvurulan DLL 'yi edinin ve kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-113">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="d1a8a-114">DLL veya başvurulan DLL, yol tarafından belirtilen bir dizinde değilse, DLL 'yi başvurulan bir dizine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-114">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a8a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1a8a-115">See also</span></span>

- [<span data-ttu-id="d1a8a-116">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="d1a8a-116">Declare Statement</span></span>](../statements/declare-statement.md)
