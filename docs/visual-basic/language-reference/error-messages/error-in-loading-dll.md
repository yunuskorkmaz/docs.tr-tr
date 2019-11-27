---
title: DLL dosyasını yüklemede hata
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329554"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="85c84-102">DLL yüklenirken hata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85c84-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="85c84-103">Dinamik bağlantı kitaplığı (DLL), bir `Declare` deyimin `Lib` yan tümcesinde belirtilen bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="85c84-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="85c84-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="85c84-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="85c84-105">Dosya DLL yürütülebilir dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="85c84-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="85c84-106">Dosya bir Microsoft Windows DLL 'i değil.</span><span class="sxs-lookup"><span data-stu-id="85c84-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="85c84-107">DLL, mevcut olmayan başka bir DLL 'ye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="85c84-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="85c84-108">DLL veya başvurulan DLL, yolda belirtilen bir dizin içinde değil.</span><span class="sxs-lookup"><span data-stu-id="85c84-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85c84-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="85c84-109">To correct this error</span></span>  
  
- <span data-ttu-id="85c84-110">Dosya bir kaynak-metin dosyasıdır ve bu nedenle DLL yürütülebilir dosyası değilse, derlenmesi ve DLL yürütülebilir bir formla ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="85c84-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="85c84-111">Dosya bir Microsoft Windows DLL değilse, Microsoft Windows eşdeğerini edinin.</span><span class="sxs-lookup"><span data-stu-id="85c84-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="85c84-112">DLL, mevcut olmayan başka bir DLL 'ye başvuruyorsa, başvurulan DLL 'yi edinin ve kullanılabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="85c84-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="85c84-113">DLL veya başvurulan DLL, yol tarafından belirtilen bir dizinde değilse, DLL 'yi başvurulan bir dizine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="85c84-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c84-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c84-114">See also</span></span>

- [<span data-ttu-id="85c84-115">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="85c84-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
