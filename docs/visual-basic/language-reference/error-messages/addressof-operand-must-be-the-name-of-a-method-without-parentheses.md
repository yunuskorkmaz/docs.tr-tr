---
title: '&#39;AddressOf&#39; işleneni bir yöntem (parantezler olmadan) adı olmalıdır'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583818"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="c6007-102">&#39;AddressOf&#39; işleneni bir yöntem (parantezler olmadan) adı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="c6007-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="c6007-103">`AddressOf` İşleci belirli bir yordamı başvuruda bulunan bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6007-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="c6007-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="c6007-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="c6007-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="c6007-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="c6007-106">Bağımsız değişkeni aşağıdaki parantezler eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6007-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="c6007-107">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="c6007-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6007-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c6007-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c6007-109">Bağımsız değişkeni aşağıdaki parantezler kaldırmak `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="c6007-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="c6007-110">Bağımsız değişkeni bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6007-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6007-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6007-111">See Also</span></span>  
 [<span data-ttu-id="c6007-112">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="c6007-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="c6007-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c6007-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
