---
title: "'<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 8ec1e704815ee10cb98d8cc20fb5982ee4b92832
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662008"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="5eb3c-102">'\<anahtar sözcüğü >' yalnızca bir örnek yöntemi içinde geçerlidir</span><span class="sxs-lookup"><span data-stu-id="5eb3c-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="5eb3c-103">`Me`, `MyClass`, Ve `MyBase` anahtar sözcükleri belirli bir sınıfın örneklerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5eb3c-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="5eb3c-104">Bunları bir paylaşılan içinde kullanamazsınız `Function` veya `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="5eb3c-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="5eb3c-105">**Hata Kimliği:** BC30043</span><span class="sxs-lookup"><span data-stu-id="5eb3c-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5eb3c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5eb3c-106">To correct this error</span></span>  
  
- <span data-ttu-id="5eb3c-107">Anahtar sözcüğü yordamdan kaldırmak veya kaldırmak `Shared` yordam bildirimi from anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5eb3c-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb3c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eb3c-108">See also</span></span>

- [<span data-ttu-id="5eb3c-109">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="5eb3c-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="5eb3c-110">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="5eb3c-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="5eb3c-111">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="5eb3c-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
