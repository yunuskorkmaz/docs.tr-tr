---
description: 'Daha fazla bilgi edinin: New Işleci (Visual Basic)'
title: Yeni İşleç
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
ms.openlocfilehash: f52dd7606127c7587173de8a78e618ceb3e4681d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665386"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="1fa7a-103">New İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fa7a-103">New Operator (Visual Basic)</span></span>

<span data-ttu-id="1fa7a-104">Yeni bir `New` nesne örneği oluşturmak için bir yan tümce tanıtır, bir tür parametresinde Oluşturucu kısıtlamasını belirtir veya bir `Sub` yordamı sınıf oluşturucusu olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-104">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fa7a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fa7a-105">Remarks</span></span>

<span data-ttu-id="1fa7a-106">Bir bildirimde veya atama ifadesinde, `New` yan tümce, örneği oluşturulabilecek tanımlanmış bir sınıf belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-106">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="1fa7a-107">Bu, sınıfın, çağıran kodun erişebileceği bir veya daha fazla Oluşturucu kullanıma sunması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-107">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="1fa7a-108">Bir `New` bildirim ifadesinde veya atama ifadesinde bir yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-108">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="1fa7a-109">İfade çalıştırıldığında, belirtilen sınıfın uygun oluşturucusunu çağırarak, sağladığınız tüm bağımsız değişkenleri geçer.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-109">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="1fa7a-110">Aşağıdaki örnek `Customer` , bir parametresi ve bir dize parametresi alan bir parametre alan, iki Oluşturucusu olan bir sınıfın örneklerini oluşturarak bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1fa7a-110">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="1fa7a-111">Diziler sınıflar olduğundan, `New` Aşağıdaki örnekte gösterildiği gibi yeni bir dizi örneği oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="1fa7a-111">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="1fa7a-112">Ortak dil çalışma zamanı (CLR), <xref:System.OutOfMemoryException> Yeni örneği oluşturmak için yeterli bellek yoksa bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-112">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="1fa7a-113">`New`Anahtar sözcüğü, sağlanan türün erişilebilir parametresiz bir oluşturucuyu kullanıma sunması gerektiğini belirtmek için tür parametresi listelerinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-113">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="1fa7a-114">Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="1fa7a-114">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="1fa7a-115">Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın adını `New` anahtar sözcüğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-115">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="1fa7a-116">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="1fa7a-116">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="1fa7a-117">`New`Anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1fa7a-117">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="1fa7a-118">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="1fa7a-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="1fa7a-119">Durumunu</span><span class="sxs-lookup"><span data-stu-id="1fa7a-119">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="1fa7a-120">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="1fa7a-120">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="1fa7a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fa7a-121">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="1fa7a-122">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="1fa7a-122">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="1fa7a-123">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="1fa7a-123">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="1fa7a-124">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="1fa7a-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1fa7a-125">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="1fa7a-125">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
