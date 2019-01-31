---
title: "'<classname>' sınıfının bilgileri yüklenemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 91f754366441cb984edf23f2c2dca4fa5c542a8e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279532"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="625c1-102">Sınıf için bilgileri yüklenemiyor\<SınıfAdı >'</span><span class="sxs-lookup"><span data-stu-id="625c1-102">Unable to load information for class '\<classname>'</span></span>
<span data-ttu-id="625c1-103">Kullanılabilir olmayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="625c1-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="625c1-104">**Hata Kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="625c1-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="625c1-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="625c1-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="625c1-106">Sınıf tanımlanır ve adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="625c1-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2.  <span data-ttu-id="625c1-107">Modülde tanımlanmış üyelerinden erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="625c1-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="625c1-108">Bazı durumlarda, burada bildirildikleri modülleri henüz yüklenmedi çünkü hata ayıklama ortamında üyeleri bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="625c1-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625c1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="625c1-109">See also</span></span>
- [<span data-ttu-id="625c1-110">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="625c1-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
