---
title: Gerekli nesne
ms.date: 07/20/2015
f1_keywords:
- vbrID424
ms.assetid: afdc660b-81a5-4c92-ac7e-9c3a3105fc16
ms.openlocfilehash: 5384dc603d51b31c252c9cad0775a453210f29ff
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873644"
---
# <a name="object-required-visual-basic"></a><span data-ttu-id="85201-102">Gerekli nesne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85201-102">Object required (Visual Basic)</span></span>

<span data-ttu-id="85201-103">Özellik ve yöntemlere yapılan başvurular genellikle açık bir nesne niteleyicisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="85201-103">References to properties and methods often require an explicit object qualifier.</span></span> <span data-ttu-id="85201-104">Bu durum böyle bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="85201-104">This is such a case.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85201-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="85201-105">To correct this error</span></span>  
  
1. <span data-ttu-id="85201-106">Bir nesne özelliğine veya yöntemine yapılan başvuruların geçerli nesne niteleyicisi olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="85201-106">Check that references to an object property or method have valid object qualifier.</span></span> <span data-ttu-id="85201-107">Bir nesne niteleyicisi sağlamazsanız bir nesne niteleyicisi belirtin.</span><span class="sxs-lookup"><span data-stu-id="85201-107">Specify an object qualifier if you didn't provide one.</span></span>  
  
2. <span data-ttu-id="85201-108">Nesne niteleyicisi yazımını denetleyin ve nesnenin kendisine başvurduğunuz programın bölümünde göründüğünden emin olun.</span><span class="sxs-lookup"><span data-stu-id="85201-108">Check the spelling of the object qualifier and make sure the object is visible in the part of the program in which you are referencing it.</span></span>  
  
3. <span data-ttu-id="85201-109">Bir ana bilgisayar uygulamasının **Dosya Aç** komutuna bir yol sağlanırsa, içindeki bağımsız değişkenlerin doğru olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="85201-109">If a path is supplied to a host application's **File Open** command, check that the arguments in it are correct.</span></span>  
  
4. <span data-ttu-id="85201-110">Nesnenin belgelerini denetleyin ve eylemin geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="85201-110">Check the object's documentation and make sure the action is valid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85201-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85201-111">See also</span></span>

- [<span data-ttu-id="85201-112">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="85201-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
