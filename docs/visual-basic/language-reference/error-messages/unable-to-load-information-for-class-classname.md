---
title: "'<classname>' sınıfının bilgileri yüklenemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 449bd34d5026dd4f9b9020123b99df81081f4331
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873507"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="a2e17-102">'\<classname>' sınıfının bilgileri yüklenemiyor</span><span class="sxs-lookup"><span data-stu-id="a2e17-102">Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="a2e17-103">Kullanılamayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e17-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="a2e17-104">**Hata kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="a2e17-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2e17-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a2e17-105">To correct this error</span></span>  
  
1. <span data-ttu-id="a2e17-106">Sınıfın tanımlandığını ve adı doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a2e17-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2. <span data-ttu-id="a2e17-107">Modülde belirtilen üyelerden birine erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="a2e17-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="a2e17-108">Bazı durumlarda, bildirildiği modüller henüz yüklenmediği için hata ayıklama ortamı üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="a2e17-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e17-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e17-109">See also</span></span>

- [<span data-ttu-id="a2e17-110">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a2e17-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
