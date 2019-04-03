---
title: "'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: af1ce858108785fa4dac6352c9e80531e86fbb23
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813970"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="4d061-102">'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)</span><span class="sxs-lookup"><span data-stu-id="4d061-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="4d061-103">`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d061-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="4d061-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="4d061-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="4d061-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="4d061-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="4d061-106">Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4d061-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="4d061-107">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="4d061-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d061-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4d061-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="4d061-109">Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="4d061-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="4d061-110">Bağımsız değişken bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4d061-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d061-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d061-111">See also</span></span>

- [<span data-ttu-id="4d061-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="4d061-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="4d061-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4d061-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
