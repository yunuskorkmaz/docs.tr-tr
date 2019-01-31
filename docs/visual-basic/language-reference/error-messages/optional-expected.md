---
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 0ad0d0890b73103a0678b13409a24190329d37d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266340"
---
# <a name="optional-expected"></a><span data-ttu-id="545f7-102">'Optional' bekleniyor</span><span class="sxs-lookup"><span data-stu-id="545f7-102">'Optional' expected</span></span>
<span data-ttu-id="545f7-103">Bir yordam bildirimi isteğe bağlı bağımsız değişkeni gerekli bir bağımsız değişkeni tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="545f7-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="545f7-104">İsteğe bağlı bir bağımsız değişkeni aşağıdaki her bağımsız değişken isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="545f7-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="545f7-105">**Hata Kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="545f7-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="545f7-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="545f7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="545f7-107">Bağımsız değişkeni gerekli olması amaçlanıyorsa, ilk isteğe bağlı bağımsız değişken bağımsız değişken listesinde öncesinde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="545f7-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="545f7-108">Bağımsız değişken isteğe bağlı olacak şekilde tasarlanmıştır kullanırsanız `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="545f7-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545f7-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="545f7-109">See also</span></span>
- [<span data-ttu-id="545f7-110">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="545f7-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
