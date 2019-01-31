---
title: "'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)"
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262120"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="93b67-102">'AddressOf' işleneni bir metot adı olmalıdır (parantezler olmadan)</span><span class="sxs-lookup"><span data-stu-id="93b67-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="93b67-103">`AddressOf` İşleci, belirli bir yordam başvuran bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93b67-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="93b67-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="93b67-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="93b67-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="93b67-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="93b67-106">Bağımsız değişkeni aşağıdaki parantez içine eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="93b67-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="93b67-107">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="93b67-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93b67-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="93b67-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="93b67-109">Bağımsız değişkeni aşağıdaki etrafındaki parantezleri kaldırın `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="93b67-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="93b67-110">Bağımsız değişken bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="93b67-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b67-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93b67-111">See also</span></span>
- [<span data-ttu-id="93b67-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="93b67-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="93b67-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="93b67-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
