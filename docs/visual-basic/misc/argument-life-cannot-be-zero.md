---
title: "' Life ' bağımsız değişkeni sıfır olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: 280571b9f9c799305efd53359e079d25d16ffd03
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087212"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="7443f-102">' Life ' bağımsız değişkeni sıfır olamaz</span><span class="sxs-lookup"><span data-stu-id="7443f-102">Argument 'Life' cannot be zero</span></span>

<span data-ttu-id="7443f-103">`Life` `Double` Varlığının yararlı ömrünün uzunluğunu belirten bir bağımsız değişkeni geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="7443f-103">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7443f-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7443f-104">To correct this error</span></span>  
  
- <span data-ttu-id="7443f-105">İfadedeki bağımsız değişkenlerin yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7443f-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="7443f-106">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılan bir sayısal değişkeni örtülü olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="7443f-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="7443f-107">Deyimdeki değişkenlerde, özellikle de diğer yordamlardan bağımsız değişken olarak geçirilen işlemler için önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7443f-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7443f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7443f-108">See also</span></span>

- [<span data-ttu-id="7443f-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="7443f-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
