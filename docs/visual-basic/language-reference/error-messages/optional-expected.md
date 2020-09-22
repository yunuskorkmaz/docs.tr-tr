---
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: e212939cf814a9ac632571b2203f2f256dea61ae
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873599"
---
# <a name="optional-expected"></a><span data-ttu-id="f1c63-102">'Optional' bekleniyor</span><span class="sxs-lookup"><span data-stu-id="f1c63-102">'Optional' expected</span></span>

<span data-ttu-id="f1c63-103">Yordam bildiriminde isteğe bağlı bir bağımsız değişken, ardından gerekli bir bağımsız değişken tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="f1c63-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="f1c63-104">İsteğe bağlı bağımsız değişkenden sonraki her bağımsız değişken de isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1c63-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="f1c63-105">**Hata kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="f1c63-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f1c63-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f1c63-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f1c63-107">Bağımsız değişkenin gerekli olması amaçlanıyorsa, bağımsız değişken listesindeki ilk isteğe bağlı bağımsız değişkenden önce onu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="f1c63-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="f1c63-108">Bağımsız değişkenin isteğe bağlı olması amaçlanıyorsa, `Optional` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1c63-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c63-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c63-109">See also</span></span>

- [<span data-ttu-id="f1c63-110">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1c63-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
