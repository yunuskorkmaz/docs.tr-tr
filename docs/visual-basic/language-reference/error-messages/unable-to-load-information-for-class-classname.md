---
title: Sınıfının bilgileri yüklenemiyor &#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 4ee58b02965bef680731f6911d8b5121fd890eb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604178"
---
# <a name="unable-to-load-information-for-class-39ltclassnamegt39"></a><span data-ttu-id="dc367-102">Sınıfının bilgileri yüklenemiyor &#39; &lt;classname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="dc367-102">Unable to load information for class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="dc367-103">Bir başvuru kullanılabilir olmayan bir sınıfa yapıldı.</span><span class="sxs-lookup"><span data-stu-id="dc367-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="dc367-104">**Hata Kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="dc367-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dc367-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dc367-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="dc367-106">Sınıf tanımlanır ve adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="dc367-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2.  <span data-ttu-id="dc367-107">Modülde tanımlanmış üyelerinden erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="dc367-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="dc367-108">Bazı durumlarda, burada bildirilen modülleri henüz yüklenmedi olmadığından üyeleri hata ayıklama ortamı bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="dc367-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc367-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc367-109">See Also</span></span>  
 [<span data-ttu-id="dc367-110">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dc367-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
