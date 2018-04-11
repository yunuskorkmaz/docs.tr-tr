---
title: '&#39; AddressOf &#39; işleneni bir yöntem (parantezler olmadan) adı olmalıdır'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="791d0-102">&#39; AddressOf &#39; işleneni bir yöntem (parantezler olmadan) adı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="791d0-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="791d0-103">`AddressOf` İşleci belirli bir yordamı başvuruda bulunan bir yordam temsilci örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="791d0-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="791d0-104">Söz dizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="791d0-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="791d0-105">`AddressOf``procedurename`</span><span class="sxs-lookup"><span data-stu-id="791d0-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="791d0-106">Bağımsız değişkeni aşağıdaki parantezler eklenen `AddressOf`, burada Hiçbiri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="791d0-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="791d0-107">**Hata Kimliği:** BC30577</span><span class="sxs-lookup"><span data-stu-id="791d0-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="791d0-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="791d0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="791d0-109">Bağımsız değişkeni aşağıdaki parantezler kaldırmak `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="791d0-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="791d0-110">Bağımsız değişkeni bir yöntem adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="791d0-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791d0-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="791d0-111">See Also</span></span>  
 [<span data-ttu-id="791d0-112">AddressOf işleci</span><span class="sxs-lookup"><span data-stu-id="791d0-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="791d0-113">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="791d0-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
