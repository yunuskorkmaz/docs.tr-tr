---
title: Hayır erişilebilir &#39;ana&#39; uygun bir imza yöntemiyle bulundu &#39; &lt;adı&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593226"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="c4e6c-102">Hayır erişilebilir &#39;ana&#39; uygun bir imza yöntemiyle bulundu &#39; &lt;adı&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="c4e6c-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="c4e6c-103">Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="c4e6c-104">`Main` olarak bildirilmelidir `Public Shared` bir sınıf ya da olarak tanımlanmışsa `Public` modülde tanımlanmış ise.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="c4e6c-105">**Hata Kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="c4e6c-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4e6c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c4e6c-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c4e6c-107">Tanımlayan bir `Public Sub Main` projeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="c4e6c-108">Olarak bildirme `Shared` içinde bir sınıf tanımlama ve yalnızca.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e6c-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4e6c-109">See Also</span></span>  
 [<span data-ttu-id="c4e6c-110">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="c4e6c-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="c4e6c-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c4e6c-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
