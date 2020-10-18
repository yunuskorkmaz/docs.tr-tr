---
title: "'<classname>' sınıfının bilgileri yüklenemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 05c3303db90a396479bc396c5c2395c3afbb59ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161614"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="dbf61-102">BC30712: ' ' sınıfının bilgileri yüklenemiyor \<classname></span><span class="sxs-lookup"><span data-stu-id="dbf61-102">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="dbf61-103">Kullanılamayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="dbf61-103">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="dbf61-104">**Hata kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="dbf61-104">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="dbf61-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dbf61-105">To correct this error</span></span>

1. <span data-ttu-id="dbf61-106">Sınıfın tanımlandığını ve adı doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="dbf61-106">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="dbf61-107">Modülde belirtilen üyelerden birine erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="dbf61-107">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="dbf61-108">Bazı durumlarda, bildirildiği modüller henüz yüklenmediği için hata ayıklama ortamı üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="dbf61-108">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbf61-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbf61-109">See also</span></span>

- [<span data-ttu-id="dbf61-110">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dbf61-110">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
