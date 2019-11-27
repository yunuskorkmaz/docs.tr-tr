---
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
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348313"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="8497a-102">New İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8497a-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="8497a-103">Yeni bir nesne örneği oluşturmak için bir `New` yan tümcesi tanıtır, bir tür parametresinde Oluşturucu kısıtlamasını belirtir veya bir `Sub` yordamını sınıf oluşturucusu olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8497a-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="8497a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8497a-104">Remarks</span></span>

<span data-ttu-id="8497a-105">Bir bildirimde veya atama ifadesinde, bir `New` yan tümcesi, örneği oluşturulabilecek tanımlanmış bir sınıf belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="8497a-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="8497a-106">Bu, sınıfın, çağıran kodun erişebileceği bir veya daha fazla Oluşturucu kullanıma sunması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8497a-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="8497a-107">Bir bildirim ifadesinde veya atama ifadesinde bir `New` yan tümcesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8497a-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="8497a-108">İfade çalıştırıldığında, belirtilen sınıfın uygun oluşturucusunu çağırarak, sağladığınız tüm bağımsız değişkenleri geçer.</span><span class="sxs-lookup"><span data-stu-id="8497a-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="8497a-109">Aşağıdaki örnek, iki Oluşturucusu olan bir `Customer` sınıfın örnekleri oluşturarak bunu gösterir ve bir parametre ve bir dize parametresi alan bir parametre alır:</span><span class="sxs-lookup"><span data-stu-id="8497a-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="8497a-110">Diziler sınıflar olduğundan, aşağıdaki örnekte gösterildiği gibi, `New` yeni bir dizi örneği oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="8497a-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="8497a-111">Yeni örneği oluşturmak için yeterli bellek yoksa ortak dil çalışma zamanı (CLR) <xref:System.OutOfMemoryException> hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8497a-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="8497a-112">`New` anahtar sözcüğü, sağlanan türün erişilebilir parametresiz bir oluşturucuyu kullanıma sunması gerektiğini belirtmek için tür parametresi listelerinde de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8497a-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="8497a-113">Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="8497a-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="8497a-114">Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamının adını `New` anahtar sözcüğüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8497a-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="8497a-115">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="8497a-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="8497a-116">`New` anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8497a-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="8497a-117">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="8497a-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="8497a-118">Durumunu</span><span class="sxs-lookup"><span data-stu-id="8497a-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="8497a-119">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="8497a-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="8497a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8497a-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="8497a-121">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8497a-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="8497a-122">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="8497a-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="8497a-123">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="8497a-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8497a-124">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="8497a-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
