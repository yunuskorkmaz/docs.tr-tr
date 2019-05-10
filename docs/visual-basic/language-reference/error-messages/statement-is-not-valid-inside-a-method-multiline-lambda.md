---
title: Deyim yöntem-çok satırlı lambda içinde geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 9e6c8ddd7851aee6d9fa1928a6854f7337b867b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593220"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="28a9b-102">Deyim yöntem/çok satırlı lambda içinde geçerli değil</span><span class="sxs-lookup"><span data-stu-id="28a9b-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="28a9b-103">Deyimi içinde geçerli değil. bir `Sub`, `Function`, özellik `Get`, veya özellik `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="28a9b-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="28a9b-104">Bazı deyimleri modül veya sınıfının düzeyinde yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="28a9b-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="28a9b-105">Diğerleri gibi `Option Strict`, ad alanı düzeyinde olmalıdır ve diğer tüm bildirimler koyun.</span><span class="sxs-lookup"><span data-stu-id="28a9b-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="28a9b-106">**Hata Kimliği:** BC30024</span><span class="sxs-lookup"><span data-stu-id="28a9b-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28a9b-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="28a9b-107">To correct this error</span></span>  
  
- <span data-ttu-id="28a9b-108">Deyim yordamdan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="28a9b-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a9b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28a9b-109">See also</span></span>

- [<span data-ttu-id="28a9b-110">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="28a9b-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="28a9b-111">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="28a9b-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="28a9b-112">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="28a9b-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="28a9b-113">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="28a9b-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
