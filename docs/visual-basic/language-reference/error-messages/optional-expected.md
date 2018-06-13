---
title: '&#39;İsteğe bağlı&#39; bekleniyor'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 52e4288255a246f78730b33beb55f6d2d83ff214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593960"
---
# <a name="39optional39-expected"></a><span data-ttu-id="25115-102">&#39;İsteğe bağlı&#39; bekleniyor</span><span class="sxs-lookup"><span data-stu-id="25115-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="25115-103">İsteğe bağlı bir bağımsız değişken bir yordam bildirimindeki gerekli bir bağımsız değişkeni tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="25115-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="25115-104">İsteğe bağlı bir bağımsız değişkeni takip her bağımsız değişken isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25115-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="25115-105">**Hata Kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="25115-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25115-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="25115-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="25115-107">Bağımsız değişkeni gerekli olması amaçlanıyorsa, ilk isteğe bağlı bağımsız değişken bağımsız değişken listesinde öncesinde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="25115-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="25115-108">Bağımsız değişken isteğe bağlı olması amaçlanmıştır kullanırsanız `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="25115-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25115-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25115-109">See Also</span></span>  
 [<span data-ttu-id="25115-110">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="25115-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
