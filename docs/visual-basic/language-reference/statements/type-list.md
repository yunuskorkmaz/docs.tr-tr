---
title: Tür Listesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: aae9135207bbd3f9d0cc7c072e423a50902c372a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751509"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="c4805-102">Tür Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4805-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="c4805-103">Belirtir *tür parametrelerindeki* için bir *genel* programlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4805-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="c4805-104">Birden çok parametre, virgüllerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c4805-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="c4805-105">Bir tür parametresi için sözdizimi aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="c4805-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4805-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4805-106">Syntax</span></span>

```
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="c4805-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c4805-107">Parts</span></span>

|<span data-ttu-id="c4805-108">Terim</span><span class="sxs-lookup"><span data-stu-id="c4805-108">Term</span></span>|<span data-ttu-id="c4805-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="c4805-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="c4805-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4805-110">Optional.</span></span> <span data-ttu-id="c4805-111">Yalnızca genel arabirimlerde ve temsilcilerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4805-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="c4805-112">Bir türü birlikte değişken kullanarak bildirebilirsiniz [kullanıma](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) anahtar sözcük veya kullanarak, değişken karşıtı [içinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c4805-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="c4805-113">Bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4805-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="c4805-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c4805-114">Required.</span></span> <span data-ttu-id="c4805-115">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="c4805-115">Name of the type parameter.</span></span> <span data-ttu-id="c4805-116">Sağlanan karşılık gelen tür bağımsız değişkeni tarafından tanımlanan bir tür tarafından değiştirilmesi bir yer tutucu budur.</span><span class="sxs-lookup"><span data-stu-id="c4805-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="c4805-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c4805-117">Optional.</span></span> <span data-ttu-id="c4805-118">Sınırlamak için sağlanan veri türü gereksinimleri listesi `typename`.</span><span class="sxs-lookup"><span data-stu-id="c4805-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="c4805-119">Birden çok kısıtlaması varsa, bunları küme ayraçlarının içine alın (`{ }`) ve bunları virgüllerle ayırın.</span><span class="sxs-lookup"><span data-stu-id="c4805-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="c4805-120">Kısıtlama listesiyle girmeniz gerekir [olarak](../../../visual-basic/language-reference/statements/as-clause.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c4805-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="c4805-121">Kullandığınız `As` listenin başına yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="c4805-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c4805-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4805-122">Remarks</span></span>

<span data-ttu-id="c4805-123">Her genel programlama öğesine en az bir tür parametre alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4805-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="c4805-124">Bir tür parametresi belirli bir tür için bir yer tutucudur (bir *oluşturulmuş öğe*) istemci kodu genel türün bir örneğini oluşturduğunda belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4805-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="c4805-125">Genel bir sınıf tanımlamak, yapı, yordam, arabirim veya temsilci.</span><span class="sxs-lookup"><span data-stu-id="c4805-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="c4805-126">Ne zaman bir genel tür tanımlama hakkında daha fazla bilgi için bkz. [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="c4805-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="c4805-127">Tür parametresi adları hakkında daha fazla bilgi için bkz. [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c4805-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="c4805-128">Kurallar</span><span class="sxs-lookup"><span data-stu-id="c4805-128">Rules</span></span>

- <span data-ttu-id="c4805-129">**Parantezler.**</span><span class="sxs-lookup"><span data-stu-id="c4805-129">**Parentheses.**</span></span> <span data-ttu-id="c4805-130">Bir tür parametresi listesi sağlayın, parantez içine almalısınız ve listesiyle girmeniz gerekir [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c4805-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="c4805-131">Kullandığınız `Of` listenin başına yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="c4805-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="c4805-132">**Kısıtlamaları.**</span><span class="sxs-lookup"><span data-stu-id="c4805-132">**Constraints.**</span></span> <span data-ttu-id="c4805-133">Listesini *kısıtlamaları* türünü bir parametre aşağıdaki öğeler herhangi bir bileşimini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="c4805-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="c4805-134">Tüm arabirimleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="c4805-134">Any number of interfaces.</span></span> <span data-ttu-id="c4805-135">Sağlanan tür bu listede her arabirimini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4805-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="c4805-136">En fazla bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="c4805-136">At most one class.</span></span> <span data-ttu-id="c4805-137">Sağlanan türü, bu sınıftan devralmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4805-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="c4805-138">`New` Anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c4805-138">The `New` keyword.</span></span> <span data-ttu-id="c4805-139">Sağlanan tür, genel tür erişip parametresiz bir oluşturucu kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4805-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="c4805-140">Bir tür parametresi bir veya daha fazla arabirimi ile kısıtlamak, bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4805-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="c4805-141">Arabirimleri uygulayan bir tür bir oluşturucu kullanıma sunmuyor ve bir oluşturucu erişim düzeyine bağlı olarak, genel tür içinde kod erişmek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4805-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="c4805-142">Her iki `Class` anahtar sözcüğü veya `Structure` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c4805-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="c4805-143">`Class` Anahtar sözcüğü genel tür parametresine geçirilen her tür bağımsız değişkenin, örneğin bir dize, dizi veya temsilci bir başvuru türü olması veya bir nesnenin oluşturulup bir sınıftan gerektirecek şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="c4805-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="c4805-144">`Structure` Anahtar sözcüğü bir yapı, numaralandırmanın veya başlangıç veri yazın örneğin genel tür parametresine geçirilen her tür bağımsız değişkenin bir değer türü olmasını gerekli kılmak için kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="c4805-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="c4805-145">Her ikisini birden içeremez `Class` ve `Structure` aynı `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="c4805-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="c4805-146">Sağlanan tür dahil, her gereksinimin karşılamalıdır `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="c4805-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="c4805-147">Her tür parametresi kısıtlamaları, diğer tür parametrelerindeki kısıtlamalar bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c4805-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="c4805-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="c4805-148">Behavior</span></span>

- <span data-ttu-id="c4805-149">**Derleme zamanı değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="c4805-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="c4805-150">Genel programlama öğeden oluşturulan tür oluşturduğunuzda, her tür parametresi için tanımlanmış bir tür sağlayın.</span><span class="sxs-lookup"><span data-stu-id="c4805-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="c4805-151">Visual Basic Derleyicisi her oluşumu için sağlanan bu tür değiştirir `typename` genel öğe içinde.</span><span class="sxs-lookup"><span data-stu-id="c4805-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="c4805-152">**Kısıtlamaları olmayışı.**</span><span class="sxs-lookup"><span data-stu-id="c4805-152">**Absence of Constraints.**</span></span> <span data-ttu-id="c4805-153">Herhangi bir tür parametresi kısıtlamaları belirtmezseniz, kodunuz tarafından desteklenen üyeleri ve işlemleri sınırlı olan [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md) bu tür parametresi için.</span><span class="sxs-lookup"><span data-stu-id="c4805-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="c4805-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4805-154">Example</span></span>

<span data-ttu-id="c4805-155">Aşağıdaki örnek, bir çatı sözlüğe yeni bir giriş eklemek için iskelet bir işlev gibi genel bir sözlük sınıf tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4805-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="c4805-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4805-156">Example</span></span>

<span data-ttu-id="c4805-157">Çünkü `dictionary` olan genel, bunu kullanan kod çeşitli nesneleri, aynı işlevlere sahip ancak farklı bir veri türü üzerinde çalışan her oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4805-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="c4805-158">Aşağıdaki örnek, bir satırı oluşturan kodu gösterir. bir `dictionary` nesnesi ile `String` girişleri ve `Integer` anahtarları.</span><span class="sxs-lookup"><span data-stu-id="c4805-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="c4805-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4805-159">Example</span></span>

<span data-ttu-id="c4805-160">Aşağıdaki örnek önceki örneği tarafından oluşturulan eşdeğer iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4805-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="c4805-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4805-161">See also</span></span>

- [<span data-ttu-id="c4805-162">,</span><span class="sxs-lookup"><span data-stu-id="c4805-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="c4805-163">New İşleci</span><span class="sxs-lookup"><span data-stu-id="c4805-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="c4805-164">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="c4805-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c4805-165">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c4805-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="c4805-166">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4805-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c4805-167">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4805-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c4805-168">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c4805-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c4805-169">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4805-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="c4805-170">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="c4805-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="c4805-171">İçinde</span><span class="sxs-lookup"><span data-stu-id="c4805-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="c4805-172">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c4805-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
