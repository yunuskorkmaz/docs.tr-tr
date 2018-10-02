---
title: Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1e771a95542153dfad0981d3198e6b4c31cdeb9
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47861711"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="d2f81-102">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2f81-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="d2f81-103">Şu anda, Visual Basic, kullanıcı tarafından filtrelenmiş özel durumu destekler.</span><span class="sxs-lookup"><span data-stu-id="d2f81-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="d2f81-104">Kullanıcı tarafından filtrelenmiş özel durum işleyicileri catch ve özel durum için tanımladığınız gereksinimlerine göre özel durumları işleyin.</span><span class="sxs-lookup"><span data-stu-id="d2f81-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="d2f81-105">Bu işleyicilerini **Catch** deyimiyle **olduğunda** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d2f81-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="d2f81-106">Bu teknik, belirli bir özel durum nesnesi için birden çok hata karşılık gelen yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d2f81-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="d2f81-107">Bu durumda, nesne, genellikle hatayla ilişkili söz konusu hata kodunu içeren bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d2f81-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="d2f81-108">Yalnızca, işlemek istediğiniz belirli hata seçmek için ifade hata kodu özelliğini kullanabilirsiniz **Catch** yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d2f81-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="d2f81-109">Aşağıdaki Visual Basic örnek gösterir **Catch/olduğunda** deyimi.</span><span class="sxs-lookup"><span data-stu-id="d2f81-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="d2f81-110">Kullanıcı tarafından filtrelenmiş yan tümcesinin ifadesi herhangi bir yolla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d2f81-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="d2f81-111">Kullanıcı tarafından filtrelenmiş ifadenin yürütülmesi sırasında bir özel durum meydana gelirse, o özel durumu atılır ve filtre ifadesi false olarak değerlendirildi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d2f81-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="d2f81-112">Bu durumda, ortak dil çalışma zamanı, geçerli özel durum işleyicisi için arama devam eder.</span><span class="sxs-lookup"><span data-stu-id="d2f81-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="d2f81-113">Özel durum ve kullanıcı tarafından filtrelenmiş yan tümceleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="d2f81-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="d2f81-114">Catch deyimi, hem özel hem de kullanıcı tarafından filtrelenmiş yan tümceleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f81-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="d2f81-115">Çalışma zamanı özel duruma önce test eder.</span><span class="sxs-lookup"><span data-stu-id="d2f81-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="d2f81-116">Özel durum başarılı olursa, çalışma zamanı kullanıcı filtresini yürütür.</span><span class="sxs-lookup"><span data-stu-id="d2f81-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="d2f81-117">Genel filtre sınıfı filtrede bildirilen değişken başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d2f81-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="d2f81-118">İki filtre yan tümcesi sırasını ters unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2f81-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="d2f81-119">Aşağıdaki Visual Basic örnek, belirli özel durum gösterir `ClassLoadException` içinde **Catch** deyimi hem de kullanıcı tarafından filtrelenmiş yan tümcesini kullanarak **olduğunda** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d2f81-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="d2f81-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f81-120">See also</span></span>

- [<span data-ttu-id="d2f81-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d2f81-121">Exceptions</span></span>](index.md)
