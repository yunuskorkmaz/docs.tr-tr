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
ms.openlocfilehash: e72f87bd4a33491df46576629971c60af4630ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571897"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="85d79-102">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="85d79-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="85d79-103">Şu anda, Visual Basic kullanıcı tarafından filtrelenmiş özel durumlar destekler.</span><span class="sxs-lookup"><span data-stu-id="85d79-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="85d79-104">Kullanıcı tarafından filtrelenmiş özel durum işleyicileri yakalamak ve gereksinimler için özel durum tanımlayan temelinde özel durumları işleme.</span><span class="sxs-lookup"><span data-stu-id="85d79-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="85d79-105">Bu işleyiciler kullanmak **Catch** deyimiyle **zaman** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="85d79-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="85d79-106">Bu yöntem, belirli özel durum nesnesi için birden çok hata karşılık gelen yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="85d79-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="85d79-107">Bu durumda, nesne genellikle şu hata ile ilişkilendirilmiş belirli hata kodunu içeren bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="85d79-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="85d79-108">Hata kodu özelliği yalnızca içinde işleyen istediğiniz belirli hata seçmek için ifade kullanabilirsiniz **Catch** yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="85d79-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="85d79-109">Aşağıdaki Visual Basic örnek gösterilmektedir **Catch/olduğunda** deyimi.</span><span class="sxs-lookup"><span data-stu-id="85d79-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="85d79-110">Kullanıcı tarafından filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde sınırlı değil.</span><span class="sxs-lookup"><span data-stu-id="85d79-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="85d79-111">Kullanıcı tarafından filtrelenmiş ifadenin yürütülmesi sırasında bir özel durum oluşursa, başka bir özel durum atılır ve filtre ifadesi false olarak değerlendirildiğinden olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="85d79-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="85d79-112">Bu durumda, ortak dil çalışma zamanı geçerli özel durumu için bir işleyici aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="85d79-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="85d79-113">Bir özel durum ve kullanıcı tarafından filtrelenmiş yan tümceleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="85d79-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="85d79-114">Catch deyimi, bir özel durum ve kullanıcı tarafından filtrelenmiş yan tümceleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85d79-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="85d79-115">Çalışma zamanı bir özel durum ilk sınar.</span><span class="sxs-lookup"><span data-stu-id="85d79-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="85d79-116">Bir özel durum başarılı olursa, çalışma zamanı kullanıcı filtresini yürütür.</span><span class="sxs-lookup"><span data-stu-id="85d79-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="85d79-117">Genel filtre sınıfı filtrede bildirilen değişken başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="85d79-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="85d79-118">İki filtre yan tümcesi sırasını tersine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="85d79-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="85d79-119">Aşağıdaki Visual Basic örnek bir özel durum gösterir `ClassLoadException` içinde **Catch** deyimi yanı sıra kullanıcı tarafından filtrelenmiş yan tümcesini kullanarak **zaman** anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="85d79-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="85d79-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85d79-120">See Also</span></span>
[<span data-ttu-id="85d79-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="85d79-121">Exceptions</span></span>](index.md)
