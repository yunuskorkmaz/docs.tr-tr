---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591994"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="3960f-102">İçinde uygun imzaya sahip hiçbir erişilebilir 'Main' yöntemi bulunamadı '\<adı >'</span><span class="sxs-lookup"><span data-stu-id="3960f-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>
<span data-ttu-id="3960f-103">Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlı.</span><span class="sxs-lookup"><span data-stu-id="3960f-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="3960f-104">`Main` olarak bildirilmelidir `Public Shared` bir sınıf veya olarak tanımlanmışsa `Public` bir modülde tanımlı değilse.</span><span class="sxs-lookup"><span data-stu-id="3960f-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="3960f-105">**Hata Kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="3960f-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3960f-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3960f-106">To correct this error</span></span>  
  
- <span data-ttu-id="3960f-107">Tanımlayan bir `Public Sub Main` projeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="3960f-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="3960f-108">Olarak bildirin `Shared` bir sınıf içinde tanımlamak ve yalnızca.</span><span class="sxs-lookup"><span data-stu-id="3960f-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3960f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3960f-109">See also</span></span>

- [<span data-ttu-id="3960f-110">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="3960f-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="3960f-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3960f-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
