---
description: "Hakkında daha fazla bilgi edinin: BC30712: ' ' sınıfı için bilgiler yüklenemiyor <classname>"
title: "'<classname>' sınıfının bilgileri yüklenemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 5325afabfd267f15f0d0497be6ef03c8f5c828c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480537"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="e0ba4-103">BC30712: ' ' sınıfının bilgileri yüklenemiyor \<classname></span><span class="sxs-lookup"><span data-stu-id="e0ba4-103">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="e0ba4-104">Kullanılamayan bir sınıfa bir başvuru yapıldı.</span><span class="sxs-lookup"><span data-stu-id="e0ba4-104">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="e0ba4-105">**Hata kimliği:** BC30712</span><span class="sxs-lookup"><span data-stu-id="e0ba4-105">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e0ba4-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e0ba4-106">To correct this error</span></span>

1. <span data-ttu-id="e0ba4-107">Sınıfın tanımlandığını ve adı doğru yazdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0ba4-107">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="e0ba4-108">Modülde belirtilen üyelerden birine erişmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="e0ba4-108">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="e0ba4-109">Bazı durumlarda, bildirildiği modüller henüz yüklenmediği için hata ayıklama ortamı üyeleri bulamaz.</span><span class="sxs-lookup"><span data-stu-id="e0ba4-109">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0ba4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0ba4-110">See also</span></span>

- [<span data-ttu-id="e0ba4-111">Visual Studio'da Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e0ba4-111">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
