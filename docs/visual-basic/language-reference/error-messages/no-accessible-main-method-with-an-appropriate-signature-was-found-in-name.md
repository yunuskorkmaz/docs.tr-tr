---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6958e778701066760aa74e3b4d566800b7527b76
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871483"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="e6b17-102">'\<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı</span><span class="sxs-lookup"><span data-stu-id="e6b17-102">No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>

<span data-ttu-id="e6b17-103">Komut satırı uygulamalarının tanımlanmış olması gerekir `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="e6b17-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="e6b17-104">`Main``Public Shared`bir sınıfta tanımlanmalı veya `Public` bir modülde tanımlanmış gibi bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e6b17-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="e6b17-105">**Hata kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="e6b17-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e6b17-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e6b17-106">To correct this error</span></span>  
  
- <span data-ttu-id="e6b17-107">`Public Sub Main`Projeniz için bir yordam tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="e6b17-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="e6b17-108">Bunu `Shared` yalnızca bir sınıf içinde tanımlarsanız, ve olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="e6b17-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b17-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b17-109">See also</span></span>

- [<span data-ttu-id="e6b17-110">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="e6b17-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="e6b17-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6b17-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
