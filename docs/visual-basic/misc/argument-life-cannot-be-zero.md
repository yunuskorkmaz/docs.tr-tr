---
title: "'Kullanım ömrü' bağımsız değişkeni sıfır olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: b6d57859d138c6a2ecda3efe1f2ed30ad32198d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667865"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="4bab9-102">'Kullanım ömrü' bağımsız değişkeni sıfır olamaz</span><span class="sxs-lookup"><span data-stu-id="4bab9-102">Argument 'Life' cannot be zero</span></span>
<span data-ttu-id="4bab9-103">Bir bağımsız değişken `Life`, olması gereken bir `Double` varlık faydalı ömrünü belirtir, geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="4bab9-103">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4bab9-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4bab9-104">To correct this error</span></span>  
  
-   <span data-ttu-id="4bab9-105">Bağımsız değişken ifadesindeki yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4bab9-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="4bab9-106">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılır, sayısal bir değişken örtük olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bab9-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="4bab9-107">Önceki değişkenleri ifadede, özellikle yordama bağımsız değişkenler olarak diğer yordamlardan geçirilen işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4bab9-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bab9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bab9-108">See also</span></span>
- [<span data-ttu-id="4bab9-109">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="4bab9-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
