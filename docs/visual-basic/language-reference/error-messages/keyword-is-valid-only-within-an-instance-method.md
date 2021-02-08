---
description: "Hakkında daha fazla bilgi edinin: BC30043: ' <keyword> ' yalnızca bir örnek yöntemi içinde geçerlidir"
title: "'<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 0bca2df44e096da016c9cb0c2031a8ef6faeb2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795982"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="30ef1-103">BC30043: ' \<keyword> ' yalnızca bir örnek yöntemi içinde geçerlidir</span><span class="sxs-lookup"><span data-stu-id="30ef1-103">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="30ef1-104">`Me`, `MyClass` Ve `MyBase` anahtar sözcükleri belirli sınıf örneklerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="30ef1-104">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="30ef1-105">Onları paylaşılan bir veya yordam içinde kullanamazsınız `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="30ef1-105">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="30ef1-106">*Hata kimliği:*\* BC30043</span><span class="sxs-lookup"><span data-stu-id="30ef1-106">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="30ef1-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="30ef1-107">To correct this error</span></span>

- <span data-ttu-id="30ef1-108">Yordamından anahtar sözcüğünü kaldırın veya `Shared` yordam bildiriminden anahtar sözcüğü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="30ef1-108">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="30ef1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30ef1-109">See also</span></span>

- [<span data-ttu-id="30ef1-110">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="30ef1-110">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="30ef1-111">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="30ef1-111">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="30ef1-112">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="30ef1-112">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
