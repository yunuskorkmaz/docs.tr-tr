---
title: "New İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="61d2d-102">New İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61d2d-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="61d2d-103">Tanıtır bir `New` yeni bir nesne örneğini oluşturmak için yan tümcesi bir tür parametresi bir oluşturucu kısıtlama belirtir veya tanımlayan bir `Sub` bir sınıf oluşturucu yordamı.</span><span class="sxs-lookup"><span data-stu-id="61d2d-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61d2d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61d2d-104">Remarks</span></span>  
 <span data-ttu-id="61d2d-105">Bildiriminde ya da atama ifadesi, bir `New` yan tümcesi içinden örneği oluşturulabilir tanımlı bir sınıf belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="61d2d-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="61d2d-106">Bu sınıf çağıran kodu erişmek için bir veya daha fazla oluşturucular kullanıma gerekir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="61d2d-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="61d2d-107">Kullanabileceğiniz bir `New` bildirimi deyimi veya atama deyiminin yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="61d2d-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="61d2d-108">Deyim çalıştırıldığında, belirtilen sınıfının verdiğiniz herhangi bir bağımsız değişken geçirme uygun oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="61d2d-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="61d2d-109">Aşağıdaki örnekte bu örnekleri oluşturarak gösterir. bir `Customer` iki Oluşturucusu vardır sınıfı, parametre almayan diğeri bir dize parametresi alan.</span><span class="sxs-lookup"><span data-stu-id="61d2d-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="61d2d-110">Diziler sınıfları olduğundan `New` yeni bir dizi örnek aşağıdaki örneklerde gösterildiği gibi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61d2d-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="61d2d-111">Ortak dil çalışma zamanı (CLR) oluşturur bir <xref:System.OutOfMemoryException> varsa yeni bir örneğini oluşturmak için bellek yetersiz hatası.</span><span class="sxs-lookup"><span data-stu-id="61d2d-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61d2d-112">`New` Anahtar sözcüğü de tür parametresi listelerinde sağlanan türü erişilebilir parametresiz bir kurucusu kullanıma gerekir belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61d2d-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="61d2d-113">Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="61d2d-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="61d2d-114">Bir sınıf için bir oluşturucu yordam oluşturmak için adını ayarlayın bir `Sub` yordamına `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="61d2d-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="61d2d-115">Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="61d2d-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="61d2d-116">`New` Anahtar sözcüğü bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="61d2d-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="61d2d-117">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="61d2d-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="61d2d-118">,</span><span class="sxs-lookup"><span data-stu-id="61d2d-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="61d2d-119">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="61d2d-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="61d2d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61d2d-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="61d2d-121">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="61d2d-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="61d2d-122">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="61d2d-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="61d2d-123">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="61d2d-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="61d2d-124">Nesne ömrü: Nesneleri oluşturma ve yok etme</span><span class="sxs-lookup"><span data-stu-id="61d2d-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
