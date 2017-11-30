---
title: "Bağımsız değişken &#39; Dönem sayısı &#39; sıfırdan büyük olmalıdır"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa19f1842bcfa82908fe79f6fda69bbc5dd9499c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="argument-39nper39-must-be-greater-than-zero"></a><span data-ttu-id="27934-102">Bağımsız değişken &#39; Dönem sayısı &#39; sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="27934-102">Argument &#39;NPer&#39; must be greater than zero</span></span>
<span data-ttu-id="27934-103">`NPer` Döndürür işlevi bir `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir anüite için dönem sayısını belirten sıfırdan büyük bir bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="27934-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27934-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27934-104">To correct this error</span></span>  
  
-   <span data-ttu-id="27934-105">İfade değişkenlerinde yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="27934-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="27934-106">Yanlış yazılmış bir değişken adı örtük olarak sıfır olarak başlatılan sayısal bir değişken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27934-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="27934-107">Özellikle yordama diğer yordamlardan bağımsız değişken olarak geçirilen değişkenleri ifadesinde önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="27934-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27934-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27934-108">See Also</span></span>  
 [<span data-ttu-id="27934-109">IN derleme değil: Dönem sayısı işlevi</span><span class="sxs-lookup"><span data-stu-id="27934-109">NOT IN BUILD: NPer Function</span></span>](http://msdn.microsoft.com/en-us/56567d16-29f7-4928-b05f-b4cd56d4fd42)  
 [<span data-ttu-id="27934-110">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="27934-110">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
