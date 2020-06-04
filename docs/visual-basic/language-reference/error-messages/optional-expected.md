---
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 411e3248409ab0184666f4efefb4ec4becf7cab1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409354"
---
# <a name="optional-expected"></a><span data-ttu-id="d41c1-102">'Optional' bekleniyor</span><span class="sxs-lookup"><span data-stu-id="d41c1-102">'Optional' expected</span></span>
<span data-ttu-id="d41c1-103">Yordam bildiriminde isteğe bağlı bir bağımsız değişken, ardından gerekli bir bağımsız değişken tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="d41c1-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="d41c1-104">İsteğe bağlı bağımsız değişkenden sonraki her bağımsız değişken de isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d41c1-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="d41c1-105">**Hata kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="d41c1-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d41c1-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d41c1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d41c1-107">Bağımsız değişkenin gerekli olması amaçlanıyorsa, bağımsız değişken listesindeki ilk isteğe bağlı bağımsız değişkenden önce onu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="d41c1-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="d41c1-108">Bağımsız değişkenin isteğe bağlı olması amaçlanıyorsa, `Optional` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d41c1-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41c1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d41c1-109">See also</span></span>

- [<span data-ttu-id="d41c1-110">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="d41c1-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
