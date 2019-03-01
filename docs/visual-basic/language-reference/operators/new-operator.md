---
title: New İşleci (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: dda23ef3ff49bd32474f39f5ae1807e57bdc2a62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980470"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="f1c1a-102">New İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1c1a-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="f1c1a-103">Tanıtır bir `New` yan tümcesi, yeni bir nesne örneği oluşturmak için bir tür parametresinde Oluşturucu kısıtlaması belirtir ya da tanımlayan bir `Sub` sınıf oluşturucusunu yordamı.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1c1a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1c1a-104">Remarks</span></span>  
 <span data-ttu-id="f1c1a-105">Bir bildirimi veya atama ifadesi bir `New` yan tümcesinin içinden örneği oluşturulabilir tanımlanmış bir sınıf belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="f1c1a-106">Bu sınıf çağıran kod erişebilen bir veya daha fazla Oluşturucu kullanıma açmalıdır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="f1c1a-107">Kullanabileceğiniz bir `New` yan tümcesinde bir bildirim deyiminin veya atama ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="f1c1a-108">Deyim çalıştırıldığında, belirtilen sınıfın verdiğiniz herhangi bir bağımsız değişken geçirme uygun oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="f1c1a-109">Aşağıdaki örnek bu örnekleri oluşturarak gösterir. bir `Customer` sınıfın iki Oluşturucusu vardır, yani parametre almayan diğeri bir dize parametresi alan.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="f1c1a-110">Diziler sınıfları olduğundan `New` aşağıdaki örneklerde gösterildiği gibi yeni bir dizi örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="f1c1a-111">Ortak dil çalışma zamanı (CLR) bir <xref:System.OutOfMemoryException> varsa yeni bir örneğini oluşturmak için yetersiz bellek hatası.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1c1a-112">`New` Anahtar sözcüğü de türü parametre listelerindeki sağlanan tür erişilebilir parametresiz bir oluşturucu kullanıma açmalıdır belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="f1c1a-113">Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="f1c1a-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="f1c1a-114">Bir sınıf için bir oluşturucu yordam oluşturmak için kümesinin adı bir `Sub` yordama `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="f1c1a-115">Daha fazla bilgi için [nesne ömrü: Nesneler nasıl oluşturulur ve imha](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="f1c1a-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="f1c1a-116">`New` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f1c1a-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f1c1a-117">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1c1a-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f1c1a-118">,</span><span class="sxs-lookup"><span data-stu-id="f1c1a-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="f1c1a-119">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="f1c1a-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1c1a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c1a-120">See also</span></span>
- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="f1c1a-121">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f1c1a-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="f1c1a-122">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="f1c1a-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="f1c1a-123">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="f1c1a-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="f1c1a-124">Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok</span><span class="sxs-lookup"><span data-stu-id="f1c1a-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
