---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: e1f95484a153bdcac9543508b7f2708dc6b7d942
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160047"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="d9d62-102">BC30737: ' ' içinde uygun imzaya sahip erişilebilir bir ' Main ' yöntemi bulunamadı \<name></span><span class="sxs-lookup"><span data-stu-id="d9d62-102">BC30737: No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>

<span data-ttu-id="d9d62-103">Komut satırı uygulamalarının tanımlanmış olması gerekir `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="d9d62-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="d9d62-104">`Main``Public Shared`bir sınıfta tanımlanmalı veya `Public` bir modülde tanımlanmış gibi bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9d62-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>

 <span data-ttu-id="d9d62-105">**Hata kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="d9d62-105">**Error ID:** BC30737</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d9d62-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d9d62-106">To correct this error</span></span>

- <span data-ttu-id="d9d62-107">`Public Sub Main`Projeniz için bir yordam tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d9d62-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="d9d62-108">Bunu `Shared` yalnızca bir sınıf içinde tanımlarsanız, ve olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="d9d62-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d62-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9d62-109">See also</span></span>

- [<span data-ttu-id="d9d62-110">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="d9d62-110">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="d9d62-111">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d9d62-111">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
