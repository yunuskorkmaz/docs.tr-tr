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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323830"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="77cfd-102">'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)</span><span class="sxs-lookup"><span data-stu-id="77cfd-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="77cfd-103">`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77cfd-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="77cfd-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="77cfd-104">The syntax is as follows.</span></span>  
  
 `AddressOf` `procedurename`  
  
 <span data-ttu-id="77cfd-105">Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77cfd-105">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="77cfd-106">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="77cfd-106">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77cfd-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="77cfd-107">To correct this error</span></span>  
  
1. <span data-ttu-id="77cfd-108">Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="77cfd-108">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="77cfd-109">Bağımsız değişken bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="77cfd-109">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cfd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77cfd-110">See also</span></span>

- [<span data-ttu-id="77cfd-111">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="77cfd-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="77cfd-112">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="77cfd-112">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
