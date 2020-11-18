---
title: Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: d98412ed651886afc54e15b346a63dc0c549abd0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827990"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="1ea97-102">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ea97-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="1ea97-103">Şu anda Visual Basic Kullanıcı tarafından filtrelenen özel durumları destekler.</span><span class="sxs-lookup"><span data-stu-id="1ea97-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="1ea97-104">Kullanıcı filtrelenmiş özel durum işleyicileri özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="1ea97-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="1ea97-105">Bu işleyiciler **catch** **ifadesini as anahtar** sözcüğüyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ea97-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="1ea97-106">Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea97-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="1ea97-107">Bu durumda, nesnesi genellikle hatayla ilişkili özel hata kodunu içeren bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1ea97-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="1ea97-108">Bu **catch** yan tümcesinde işlemek istediğiniz belirli bir hatayı seçmek için ifadesindeki hata kodu özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ea97-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="1ea97-109">Aşağıdaki Visual Basic örnek, **catch/** while ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ea97-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="1ea97-110">Kullanıcı filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="1ea97-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="1ea97-111">Kullanıcı tarafından filtrelenen ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1ea97-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="1ea97-112">Bu durumda, ortak dil çalışma zamanı, geçerli özel durum için bir işleyici aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="1ea97-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="1ea97-113">Belirli özel durumu ve User-Filtered yan tümcelerini birleştirme</span><span class="sxs-lookup"><span data-stu-id="1ea97-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="1ea97-114">Catch ifadesinde hem belirli özel durum hem de Kullanıcı tarafından filtrelenmiş yan tümceler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea97-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="1ea97-115">Çalışma zamanı, önce belirli özel durumu sınar.</span><span class="sxs-lookup"><span data-stu-id="1ea97-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="1ea97-116">Belirli özel durum başarılı olursa, çalışma zamanı Kullanıcı filtresini yürütür.</span><span class="sxs-lookup"><span data-stu-id="1ea97-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="1ea97-117">Genel filtre, sınıf filtresinde belirtilen değişkene bir başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea97-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="1ea97-118">İki filtre yan tümcelerinin sırasının geri çevrilmeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1ea97-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="1ea97-119">Aşağıdaki Visual Basic örnek, catch deyimindeki özel durumun `ClassLoadException` yanı sıra **Catch** as anahtar sözcüğünü kullanan kullanıcı tarafından filtrelenmiş yan tümce gösterir. **When**</span><span class="sxs-lookup"><span data-stu-id="1ea97-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="1ea97-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea97-120">See also</span></span>

- [<span data-ttu-id="1ea97-121">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="1ea97-121">Exceptions</span></span>](index.md)
