---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: f5053bddf4b9ba791ad6d0733e1dd89c4ded91bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818364"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="c33c0-102">İçinde uygun imzaya sahip hiçbir erişilebilir 'Main' yöntemi bulunamadı '\<adı >'</span><span class="sxs-lookup"><span data-stu-id="c33c0-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="c33c0-103">Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlı.</span><span class="sxs-lookup"><span data-stu-id="c33c0-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="c33c0-104">`Main` olarak bildirilmelidir `Public Shared` bir sınıf veya olarak tanımlanmışsa `Public` bir modülde tanımlı değilse.</span><span class="sxs-lookup"><span data-stu-id="c33c0-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="c33c0-105">**Hata Kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="c33c0-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c33c0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c33c0-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c33c0-107">Tanımlayan bir `Public Sub Main` projeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="c33c0-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="c33c0-108">Olarak bildirin `Shared` bir sınıf içinde tanımlamak ve yalnızca.</span><span class="sxs-lookup"><span data-stu-id="c33c0-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c33c0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c33c0-109">See also</span></span>

- [<span data-ttu-id="c33c0-110">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="c33c0-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="c33c0-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c33c0-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
