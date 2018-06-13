---
title: Bağımsız değişken &#39;dönem sayısı&#39; sıfırdan büyük olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 5939262d2a58a17d8af88ebc0ba0c7597983e4aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601198"
---
# <a name="argument-39nper39-must-be-greater-than-zero"></a><span data-ttu-id="17a85-102">Bağımsız değişken &#39;dönem sayısı&#39; sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="17a85-102">Argument &#39;NPer&#39; must be greater than zero</span></span>
<span data-ttu-id="17a85-103">`NPer` Döndürür işlevi bir `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir anüite için dönem sayısını belirten sıfırdan büyük bir bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="17a85-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17a85-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="17a85-104">To correct this error</span></span>  
  
-   <span data-ttu-id="17a85-105">İfade değişkenlerinde yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="17a85-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="17a85-106">Yanlış yazılmış bir değişken adı örtük olarak sıfır olarak başlatılan sayısal bir değişken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17a85-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="17a85-107">Özellikle yordama diğer yordamlardan bağımsız değişken olarak geçirilen değişkenleri ifadesinde önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="17a85-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a85-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17a85-108">See Also</span></span>  
 [<span data-ttu-id="17a85-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="17a85-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
