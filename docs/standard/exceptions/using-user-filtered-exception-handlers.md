---
title: Kullanıcı tarafından filtrelenmiş özel durum işleyicilerini kullanma
description: C# ve Visual Basic Kullanıcı filtrelenmiş özel durum işleyicilerini nasıl kullanacağınızı öğrenin.
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512677"
---
# <a name="use-user-filtered-exception-handlers"></a><span data-ttu-id="98a52-103">Kullanıcı tarafından filtrelenmiş özel durum işleyicilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="98a52-103">Use user-filtered exception handlers</span></span>

<span data-ttu-id="98a52-104">Kullanıcı filtrelenmiş özel durum işleyicileri özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler.</span><span class="sxs-lookup"><span data-stu-id="98a52-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="98a52-105">Bu işleyiciler, `catch` ifadesini `when` anahtar sözcüğüyle ( `Catch` ve `When` Visual Basic) kullanır.</span><span class="sxs-lookup"><span data-stu-id="98a52-105">These handlers use the `catch` statement with the `when` keyword (`Catch` and `When` in Visual Basic).</span></span>  
  
 <span data-ttu-id="98a52-106">Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="98a52-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="98a52-107">Bu durumda, nesnesi genellikle hatayla ilişkili özel hata kodunu içeren bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98a52-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="98a52-108">Deyimdeki hata kodu özelliğini yalnızca bu yan tümce içinde işlemek istediğiniz belirli hatayı seçmek için kullanabilirsiniz `catch` .</span><span class="sxs-lookup"><span data-stu-id="98a52-108">You can use the error code property in the expression to select only the particular error you want to handle in that `catch` clause.</span></span>  
  
 <span data-ttu-id="98a52-109">Aşağıdaki örnek, ifadesini gösterir `catch` / `when` .</span><span class="sxs-lookup"><span data-stu-id="98a52-109">The following example illustrates the `catch`/`when` statement.</span></span>

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="98a52-110">Kullanıcı filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="98a52-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="98a52-111">Kullanıcı tarafından filtrelenen ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="98a52-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="98a52-112">Bu durumda, ortak dil çalışma zamanı, geçerli özel durum için bir işleyici aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="98a52-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="98a52-113">Belirli özel durumu ve kullanıcı filtrelenmiş yan tümceleri birleştirme</span><span class="sxs-lookup"><span data-stu-id="98a52-113">Combine the specific exception and the user-filtered clauses</span></span>  

 <span data-ttu-id="98a52-114">Bir `catch` ifade, hem belirli özel durumu hem de Kullanıcı tarafından filtrelenmiş yan tümceleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="98a52-114">A `catch` statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="98a52-115">Çalışma zamanı, önce belirli özel durumu sınar.</span><span class="sxs-lookup"><span data-stu-id="98a52-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="98a52-116">Belirli özel durum başarılı olursa, çalışma zamanı Kullanıcı filtresini yürütür.</span><span class="sxs-lookup"><span data-stu-id="98a52-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="98a52-117">Genel filtre, sınıf filtresinde belirtilen değişkene bir başvuru içerebilir.</span><span class="sxs-lookup"><span data-stu-id="98a52-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="98a52-118">İki filtre yan tümcelerinin sırasının geri çevrilmeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="98a52-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="98a52-119">Aşağıdaki örnek, **catch** deyimindeki belirli bir özel **durumu ve while anahtar sözcüğünü** kullanan kullanıcı filtrelenmiş yan tümceyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="98a52-119">The following example shows a specific exception in the **catch** statement as well as the user-filtered clause using the **when** keyword.</span></span>  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="98a52-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98a52-120">See also</span></span>

- [<span data-ttu-id="98a52-121">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="98a52-121">Exceptions</span></span>](index.md)
