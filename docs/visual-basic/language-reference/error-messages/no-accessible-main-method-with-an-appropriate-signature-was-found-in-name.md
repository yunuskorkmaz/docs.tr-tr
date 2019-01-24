---
title: Hiçbir erişilebilir &#39;ana&#39; içinde uygun imzaya sahip yöntemi bulundu &#39; &lt;adı&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 3398195ef9d503e47ab569ff85cb2a827c4270f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501496"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="39d9d-102">Hiçbir erişilebilir &#39;ana&#39; içinde uygun imzaya sahip yöntemi bulundu &#39; &lt;adı&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="39d9d-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="39d9d-103">Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlı.</span><span class="sxs-lookup"><span data-stu-id="39d9d-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="39d9d-104">`Main` olarak bildirilmelidir `Public Shared` bir sınıf veya olarak tanımlanmışsa `Public` bir modülde tanımlı değilse.</span><span class="sxs-lookup"><span data-stu-id="39d9d-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="39d9d-105">**Hata Kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="39d9d-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39d9d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="39d9d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="39d9d-107">Tanımlayan bir `Public Sub Main` projeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="39d9d-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="39d9d-108">Olarak bildirin `Shared` bir sınıf içinde tanımlamak ve yalnızca.</span><span class="sxs-lookup"><span data-stu-id="39d9d-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d9d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39d9d-109">See also</span></span>
- [<span data-ttu-id="39d9d-110">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="39d9d-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="39d9d-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="39d9d-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
