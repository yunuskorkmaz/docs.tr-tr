---
description: "Şu konuda daha fazla bilgi edinin: BC30737: ' ' içinde uygun imzaya sahip erişilebilir bir ' Main ' yöntemi bulunamadı <name>"
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 5ff79c1b7589f6b67492ad640179f7a852a2f381
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483527"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="ee793-103">BC30737: ' ' içinde uygun imzaya sahip erişilebilir bir ' Main ' yöntemi bulunamadı \<name></span><span class="sxs-lookup"><span data-stu-id="ee793-103">BC30737: No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>

<span data-ttu-id="ee793-104">Komut satırı uygulamalarının tanımlanmış olması gerekir `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="ee793-104">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="ee793-105">`Main``Public Shared`bir sınıfta tanımlanmalı veya `Public` bir modülde tanımlanmış gibi bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ee793-105">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>

 <span data-ttu-id="ee793-106">**Hata kimliği:** BC30737</span><span class="sxs-lookup"><span data-stu-id="ee793-106">**Error ID:** BC30737</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ee793-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ee793-107">To correct this error</span></span>

- <span data-ttu-id="ee793-108">`Public Sub Main`Projeniz için bir yordam tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ee793-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="ee793-109">Bunu `Shared` yalnızca bir sınıf içinde tanımlarsanız, ve olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="ee793-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee793-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee793-110">See also</span></span>

- [<span data-ttu-id="ee793-111">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="ee793-111">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="ee793-112">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ee793-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
