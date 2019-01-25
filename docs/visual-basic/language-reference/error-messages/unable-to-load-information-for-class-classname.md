---
title: Sınıfının bilgileri yüklenemiyor &#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 368484d9138d1ae10efb8c63f6cfaa6bcefa6ed8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528972"
---
# <a name="unable-to-load-information-for-class-39ltclassnamegt39"></a><span data-ttu-id="e926f-102">Sınıfının bilgileri yüklenemiyor &#39; &lt;classname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e926f-102">Unable to load information for class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="e926f-103">Kullanılabilir olmayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="e926f-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="e926f-104">**Hata Kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="e926f-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e926f-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e926f-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="e926f-106">Sınıf tanımlanır ve adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e926f-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2.  <span data-ttu-id="e926f-107">Modülde tanımlanmış üyelerinden erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="e926f-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="e926f-108">Bazı durumlarda, burada bildirildikleri modülleri henüz yüklenmedi çünkü hata ayıklama ortamında üyeleri bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="e926f-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e926f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e926f-109">See also</span></span>
- [<span data-ttu-id="e926f-110">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e926f-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
