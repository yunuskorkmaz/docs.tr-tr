---
title: '&#39;İsteğe bağlı&#39; bekleniyor'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 46bd84e2bcf5c5bea11a5c9d8b6e9254c49e3021
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642483"
---
# <a name="39optional39-expected"></a><span data-ttu-id="b3c46-102">&#39;İsteğe bağlı&#39; bekleniyor</span><span class="sxs-lookup"><span data-stu-id="b3c46-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="b3c46-103">Bir yordam bildirimi isteğe bağlı bağımsız değişkeni gerekli bir bağımsız değişkeni tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="b3c46-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="b3c46-104">İsteğe bağlı bir bağımsız değişkeni aşağıdaki her bağımsız değişken isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3c46-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="b3c46-105">**Hata Kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="b3c46-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3c46-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b3c46-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b3c46-107">Bağımsız değişkeni gerekli olması amaçlanıyorsa, ilk isteğe bağlı bağımsız değişken bağımsız değişken listesinde öncesinde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="b3c46-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="b3c46-108">Bağımsız değişken isteğe bağlı olacak şekilde tasarlanmıştır kullanırsanız `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b3c46-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c46-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c46-109">See also</span></span>
- [<span data-ttu-id="b3c46-110">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3c46-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
