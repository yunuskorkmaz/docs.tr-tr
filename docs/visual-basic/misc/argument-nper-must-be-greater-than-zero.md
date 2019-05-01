---
title: Bağımsız değişken 'NPer' sıfırdan büyük olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 6f54a2da0eb0c1cc31a4aa536fdcb59026240a25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977151"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="4f871-102">Bağımsız değişken 'NPer' sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="4f871-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="4f871-103">`NPer` Döndüren bir işlev bir `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir anüite için dönem sayısını belirten bir bağımsız değişken sıfırdan büyük gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4f871-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f871-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4f871-104">To correct this error</span></span>  
  
- <span data-ttu-id="4f871-105">Bağımsız değişken ifadesindeki yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4f871-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="4f871-106">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılır, sayısal bir değişken örtük olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f871-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="4f871-107">Önceki değişkenleri ifadede, özellikle yordama bağımsız değişkenler olarak diğer yordamlardan geçirilen işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4f871-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f871-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f871-108">See also</span></span>

- [<span data-ttu-id="4f871-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="4f871-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
