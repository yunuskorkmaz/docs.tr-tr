---
title: "Let Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="5708e-102">Let Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5708e-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="5708e-103">Bir değeri hesaplar ve sorgu içinde yeni bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="5708e-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5708e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5708e-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="5708e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5708e-105">Parts</span></span>  
  
|<span data-ttu-id="5708e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5708e-106">Term</span></span>|<span data-ttu-id="5708e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5708e-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="5708e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5708e-108">Required.</span></span> <span data-ttu-id="5708e-109">Sağlanan ifade sonuçlarını başvurmak için kullanılan bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="5708e-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="5708e-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5708e-110">Required.</span></span> <span data-ttu-id="5708e-111">Değerlendirilecek ve belirtilen değişkenine atanan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5708e-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5708e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5708e-112">Remarks</span></span>  
 <span data-ttu-id="5708e-113">`Let` Yan tümcesi, her biri için değerleri sorgu sonucu ve bir diğer ad kullanarak başvuru işlem olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5708e-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="5708e-114">Diğer ad diğer yan tümcelerinde gibi kullanılabilir `Where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5708e-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="5708e-115">`Let` Yan tümcesi, çünkü sorguda bir ifade yan tümcesi için diğer ad belirtin ve ifade yan tümcesinde kullanılan her zaman diğer adı yerine okunması daha kolay olan bir sorgu deyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5708e-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="5708e-116">Herhangi bir sayıda içerebilir `variable` ve `expression` atamalarını `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5708e-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="5708e-117">Her bir atama virgülle (,) ayırın.</span><span class="sxs-lookup"><span data-stu-id="5708e-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5708e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="5708e-118">Example</span></span>  
 <span data-ttu-id="5708e-119">Aşağıdaki kod örneğinde `Let` yüzde 10 indirim ürünlerine hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5708e-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5708e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5708e-120">See Also</span></span>  
 [<span data-ttu-id="5708e-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="5708e-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="5708e-122">Sorguları</span><span class="sxs-lookup"><span data-stu-id="5708e-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="5708e-123">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="5708e-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="5708e-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5708e-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="5708e-125">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5708e-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
