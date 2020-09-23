---
title: "' Taksit_sayısı ' bağımsız değişkeni sıfırdan büyük olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: f0185e30cb711472105955f5febf8d7702b29c72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087147"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="d1e03-102">' Taksit_sayısı ' bağımsız değişkeni sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="d1e03-102">Argument 'NPer' must be greater than zero</span></span>

<span data-ttu-id="d1e03-103">`NPer` `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir Anüite için dönem sayısını belirten işlevi, sıfırdan büyük bir bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d1e03-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1e03-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d1e03-104">To correct this error</span></span>  
  
- <span data-ttu-id="d1e03-105">İfadedeki bağımsız değişkenlerin yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d1e03-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="d1e03-106">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılan bir sayısal değişkeni örtülü olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d1e03-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="d1e03-107">Deyimdeki değişkenlerde, özellikle de diğer yordamlardan bağımsız değişken olarak geçirilen işlemler için önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d1e03-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e03-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e03-108">See also</span></span>

- [<span data-ttu-id="d1e03-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="d1e03-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
