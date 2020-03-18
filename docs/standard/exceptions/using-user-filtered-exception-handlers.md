---
title: Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708459"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="04265-102">Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="04265-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="04265-103">Şu anda Visual Basic, kullanıcı tarafından filtre uygulanmış özel durumları destekler.</span><span class="sxs-lookup"><span data-stu-id="04265-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="04265-104">Kullanıcı tarafından filtre uygulanmış özel durum işleyicileri, özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="04265-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="04265-105">Bu işleyiciler Catch **deyimini** **When** anahtar sözcüğüyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="04265-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="04265-106">Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="04265-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="04265-107">Bu durumda, nesne genellikle hata ile ilişkili belirli hata kodu içeren bir özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="04265-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="04265-108">İfadedeki hata kodu özelliğini yalnızca bu **Catch** yan tümcesinde işlemek istediğiniz belirli hatayı seçmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04265-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="04265-109">Aşağıdaki Visual Basic örneği **Catch/When** deyimini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="04265-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="04265-110">Kullanıcı tarafından filtre uygulanmış yan tümcenin ifadesi hiçbir şekilde kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="04265-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="04265-111">Kullanıcı tarafından filtre uygulanan ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilmiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="04265-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="04265-112">Bu durumda, ortak dil çalışma zamanı geçerli özel durum için bir işleyici aramaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="04265-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="04265-113">Özel Özel Durum ve Kullanıcı Filtreuygulanan Yan Tümceleri Birleştirme</span><span class="sxs-lookup"><span data-stu-id="04265-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="04265-114">Catch deyimi hem özel özel durum hem de kullanıcı tarafından filtre uygulanmış yan tümceleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="04265-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="04265-115">Çalışma zamanı önce belirli özel durumu sınar.</span><span class="sxs-lookup"><span data-stu-id="04265-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="04265-116">Belirli bir özel durum başarılı olursa, çalışma zamanı kullanıcı filtresini yürütür.</span><span class="sxs-lookup"><span data-stu-id="04265-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="04265-117">Genel filtre, sınıf filtresinde bildirilen değişkene bir başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="04265-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="04265-118">İki filtre yan tümcesinin sırasının geri alınamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="04265-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="04265-119">Aşağıdaki Visual Basic örneği, `ClassLoadException` **Catch** deyimindeki özel özel durumu ve **Zaman** anahtar sözcük lerini kullanarak kullanıcı tarafından filtre uygulanmış yan tümcesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="04265-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="04265-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04265-120">See also</span></span>

- [<span data-ttu-id="04265-121">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="04265-121">Exceptions</span></span>](index.md)
