---
title: Bağımsız değişken 'NPer' sıfırdan büyük olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 43f700c28d5ffce8dc8b33651ce69493d9742272
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659092"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="b742a-102">Bağımsız değişken 'NPer' sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="b742a-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="b742a-103">`NPer` Döndüren bir işlev bir `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir anüite için dönem sayısını belirten bir bağımsız değişken sıfırdan büyük gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b742a-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b742a-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b742a-104">To correct this error</span></span>  
  
- <span data-ttu-id="b742a-105">Bağımsız değişken ifadesindeki yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b742a-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="b742a-106">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılır, sayısal bir değişken örtük olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b742a-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="b742a-107">Önceki değişkenleri ifadede, özellikle yordama bağımsız değişkenler olarak diğer yordamlardan geçirilen işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b742a-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b742a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b742a-108">See also</span></span>

- [<span data-ttu-id="b742a-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="b742a-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
