---
title: "&#39; isteğe bağlı &#39; Beklenen"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords: BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e84371935fdd2d558e6828c05fa952b9cc4cf4f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39optional39-expected"></a><span data-ttu-id="33375-102">&#39; isteğe bağlı &#39; Beklenen</span><span class="sxs-lookup"><span data-stu-id="33375-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="33375-103">İsteğe bağlı bir bağımsız değişken bir yordam bildirimindeki gerekli bir bağımsız değişkeni tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="33375-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="33375-104">İsteğe bağlı bir bağımsız değişkeni takip her bağımsız değişken isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33375-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="33375-105">**Hata Kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="33375-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33375-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="33375-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="33375-107">Bağımsız değişkeni gerekli olması amaçlanıyorsa, ilk isteğe bağlı bağımsız değişken bağımsız değişken listesinde öncesinde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="33375-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="33375-108">Bağımsız değişken isteğe bağlı olması amaçlanmıştır kullanırsanız `Optional` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="33375-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33375-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33375-109">See Also</span></span>  
 [<span data-ttu-id="33375-110">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="33375-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
