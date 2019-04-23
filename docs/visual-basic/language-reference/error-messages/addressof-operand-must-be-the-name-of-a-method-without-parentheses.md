---
title: "'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323830"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="04a20-102">'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)</span><span class="sxs-lookup"><span data-stu-id="04a20-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="04a20-103">`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04a20-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="04a20-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="04a20-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="04a20-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="04a20-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="04a20-106">Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="04a20-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="04a20-107">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="04a20-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04a20-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="04a20-108">To correct this error</span></span>  
  
1. <span data-ttu-id="04a20-109">Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="04a20-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="04a20-110">Bağımsız değişken bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="04a20-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a20-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a20-111">See also</span></span>

- [<span data-ttu-id="04a20-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="04a20-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="04a20-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="04a20-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
