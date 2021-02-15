---
description: "Hakkında daha fazla bilgi edinin: ' Life ' bağımsız değişkeni sıfır olamaz"
title: "' Life ' bağımsız değişkeni sıfır olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: e07c31ab73d6ad3f055adcbf7f4f67d48311c6cd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474882"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="31627-103">' Life ' bağımsız değişkeni sıfır olamaz</span><span class="sxs-lookup"><span data-stu-id="31627-103">Argument 'Life' cannot be zero</span></span>

<span data-ttu-id="31627-104">`Life` `Double` Varlığının yararlı ömrünün uzunluğunu belirten bir bağımsız değişkeni geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="31627-104">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31627-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="31627-105">To correct this error</span></span>  
  
- <span data-ttu-id="31627-106">İfadedeki bağımsız değişkenlerin yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="31627-106">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="31627-107">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılan bir sayısal değişkeni örtülü olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="31627-107">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="31627-108">Deyimdeki değişkenlerde, özellikle de diğer yordamlardan bağımsız değişken olarak geçirilen işlemler için önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="31627-108">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31627-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31627-109">See also</span></span>

- [<span data-ttu-id="31627-110">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="31627-110">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
