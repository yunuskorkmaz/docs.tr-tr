---
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874377"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="6f05e-102">DLL yüklenirken hata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f05e-102">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="6f05e-103">Dinamik bağlantı kitaplığı (DLL), `Lib` bir deyimin yan tümcesinde belirtilen bir kitaplıktır `Declare` .</span><span class="sxs-lookup"><span data-stu-id="6f05e-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="6f05e-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f05e-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="6f05e-105">Dosya DLL yürütülebilir dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="6f05e-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="6f05e-106">Dosya bir Microsoft Windows DLL 'i değil.</span><span class="sxs-lookup"><span data-stu-id="6f05e-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="6f05e-107">DLL, mevcut olmayan başka bir DLL 'ye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6f05e-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="6f05e-108">DLL veya başvurulan DLL, yolda belirtilen bir dizin içinde değil.</span><span class="sxs-lookup"><span data-stu-id="6f05e-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f05e-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6f05e-109">To correct this error</span></span>  
  
- <span data-ttu-id="6f05e-110">Dosya bir kaynak-metin dosyasıdır ve bu nedenle DLL yürütülebilir dosyası değilse, derlenmesi ve DLL yürütülebilir bir formla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f05e-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="6f05e-111">Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğerini edinin.</span><span class="sxs-lookup"><span data-stu-id="6f05e-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="6f05e-112">DLL, mevcut olmayan başka bir DLL 'ye başvuruyorsa, başvurulan DLL 'yi edinin ve kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="6f05e-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="6f05e-113">DLL veya başvurulan DLL, yol tarafından belirtilen bir dizinde değilse, DLL 'yi başvurulan bir dizine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="6f05e-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f05e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f05e-114">See also</span></span>

- [<span data-ttu-id="6f05e-115">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f05e-115">Declare Statement</span></span>](../statements/declare-statement.md)
