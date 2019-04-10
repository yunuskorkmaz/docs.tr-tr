---
title: "'<classname>' sınıfının bilgileri yüklenemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 42f31df7f4bc849374d8beb09e17394c3cdd5ec4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318207"
---
# <a name="unable-to-load-information-for-class-classname"></a><span data-ttu-id="eeebd-102">Sınıf için bilgileri yüklenemiyor\<SınıfAdı >'</span><span class="sxs-lookup"><span data-stu-id="eeebd-102">Unable to load information for class '\<classname>'</span></span>
<span data-ttu-id="eeebd-103">Kullanılabilir olmayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="eeebd-103">A reference was made to a class that is not available.</span></span>  
  
 <span data-ttu-id="eeebd-104">**Hata Kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="eeebd-104">**Error ID:** BC30712</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eeebd-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="eeebd-105">To correct this error</span></span>  
  
1. <span data-ttu-id="eeebd-106">Sınıf tanımlanır ve adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="eeebd-106">Verify that the class is defined and that you spelled the name correctly.</span></span>  
  
2. <span data-ttu-id="eeebd-107">Modülde tanımlanmış üyelerinden erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="eeebd-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="eeebd-108">Bazı durumlarda, burada bildirildikleri modülleri henüz yüklenmedi çünkü hata ayıklama ortamında üyeleri bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="eeebd-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeebd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeebd-109">See also</span></span>

- [<span data-ttu-id="eeebd-110">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="eeebd-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
