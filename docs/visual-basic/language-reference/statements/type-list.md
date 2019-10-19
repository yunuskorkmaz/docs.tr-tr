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
ms.openlocfilehash: a0d489684b8f98e871211e6d0d95d42284275954
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582892"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="046de-102">Tür Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="046de-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="046de-103">*Genel* programlama öğesi için *tür parametrelerini* belirtir.</span><span class="sxs-lookup"><span data-stu-id="046de-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="046de-104">Birden çok parametre virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="046de-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="046de-105">Bir tür parametresi için sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="046de-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="046de-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="046de-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="046de-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="046de-107">Parts</span></span>

|<span data-ttu-id="046de-108">Terim</span><span class="sxs-lookup"><span data-stu-id="046de-108">Term</span></span>|<span data-ttu-id="046de-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="046de-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="046de-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="046de-110">Optional.</span></span> <span data-ttu-id="046de-111">Yalnızca Genel arabirimlerde ve temsilcilerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="046de-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="046de-112">[In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) anahtar sözcüğünü kullanarak [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) anahtar sözcüğünü veya değişken varyantını kullanarak bir tür covaryant bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="046de-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="046de-113">Bkz. [Kovaryans ve değişken varyansı](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="046de-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="046de-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="046de-114">Required.</span></span> <span data-ttu-id="046de-115">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="046de-115">Name of the type parameter.</span></span> <span data-ttu-id="046de-116">Bu, karşılık gelen tür bağımsız değişkeni tarafından sağlanan tanımlı bir türle değiştirilmesini sağlamak için bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="046de-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="046de-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="046de-117">Optional.</span></span> <span data-ttu-id="046de-118">@No__t_0 için sağlanabilecek veri türünü kısıtlayan gereksinimlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="046de-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="046de-119">Birden çok kısıtlamaınız varsa bunları küme ayraçları (`{ }`) içine alın ve bunları virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="046de-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="046de-120">Kısıtlama listesini [as](../../../visual-basic/language-reference/statements/as-clause.md) anahtar sözcüğüyle birlikte tanıtmalısınız.</span><span class="sxs-lookup"><span data-stu-id="046de-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="046de-121">@No__t_0, listenin başlangıcında yalnızca bir kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="046de-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="046de-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="046de-122">Remarks</span></span>

<span data-ttu-id="046de-123">Her genel programlama öğesi en az bir tür parametresi almalıdır.</span><span class="sxs-lookup"><span data-stu-id="046de-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="046de-124">Tür parametresi, bir genel türün örneğini oluşturduğunda istemci kodunun belirttiği belirli bir tür ( *oluşturulmuş bir öğe*) için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="046de-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="046de-125">Bir genel sınıf, yapı, arabirim, yordam veya temsilci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="046de-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="046de-126">Genel bir türün ne zaman tanımlanacağı hakkında daha fazla bilgi için, bkz. [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="046de-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="046de-127">Tür parametresi adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="046de-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="046de-128">Kurallar</span><span class="sxs-lookup"><span data-stu-id="046de-128">Rules</span></span>

- <span data-ttu-id="046de-129">**Ayraçlar.**</span><span class="sxs-lookup"><span data-stu-id="046de-129">**Parentheses.**</span></span> <span data-ttu-id="046de-130">Bir tür parametre listesi [sağlarsanız, onu](../../../visual-basic/language-reference/statements/of-clause.md) parantez içine almalısınız ve listeyi anahtar kelimesiyle birlikte almalısınız.</span><span class="sxs-lookup"><span data-stu-id="046de-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="046de-131">@No__t_0, listenin başlangıcında yalnızca bir kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="046de-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="046de-132">**Kısıtlamaları.**</span><span class="sxs-lookup"><span data-stu-id="046de-132">**Constraints.**</span></span> <span data-ttu-id="046de-133">Bir tür parametresindeki *kısıtlamaların* listesi, aşağıdaki öğeleri herhangi bir kombinasyonda içerebilir:</span><span class="sxs-lookup"><span data-stu-id="046de-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="046de-134">Herhangi bir sayıda arabirim.</span><span class="sxs-lookup"><span data-stu-id="046de-134">Any number of interfaces.</span></span> <span data-ttu-id="046de-135">Sağlanan tür, bu listedeki her arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="046de-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="046de-136">En fazla bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="046de-136">At most one class.</span></span> <span data-ttu-id="046de-137">Sağlanan tür bu sınıftan devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="046de-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="046de-138">@No__t_0 anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="046de-138">The `New` keyword.</span></span> <span data-ttu-id="046de-139">Sağlanan tür, genel türünün erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="046de-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="046de-140">Bir tür parametresini bir veya daha fazla arabirim ile sınırlandırdıysanız, bu faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="046de-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="046de-141">Arabirimleri uygulayan bir tür bir oluşturucuyu kullanıma sunmayabilir ve bir oluşturucunun erişim düzeyine bağlı olarak, genel türdeki kod buna erişemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="046de-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="046de-142">@No__t_0 anahtar sözcüğü ya da `Structure` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="046de-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="046de-143">@No__t_0 anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir başvuru türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir String, array veya Delegate veya bir sınıftan oluşturulmuş bir nesne.</span><span class="sxs-lookup"><span data-stu-id="046de-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="046de-144">@No__t_0 anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir değer türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir yapı, sabit listesi veya Öğesel veri türü.</span><span class="sxs-lookup"><span data-stu-id="046de-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="046de-145">@No__t_0 ve `Structure` aynı `constraintlist` dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="046de-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="046de-146">Sağlanan tür, `constraintlist` eklediğiniz her gereksinimi karşılamalıdır.</span><span class="sxs-lookup"><span data-stu-id="046de-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="046de-147">Her tür parametresindeki kısıtlamalar, diğer tür parametrelerinin kısıtlamalarından bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="046de-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="046de-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="046de-148">Behavior</span></span>

- <span data-ttu-id="046de-149">**Derleme zamanı değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="046de-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="046de-150">Genel programlama öğesinden oluşturulmuş bir tür oluşturduğunuzda, her tür parametresi için tanımlı bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="046de-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="046de-151">Visual Basic derleyici, genel öğe içindeki her `typename` oluşumu için sağlanan türü kullanır.</span><span class="sxs-lookup"><span data-stu-id="046de-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="046de-152">**Kısıtlamaların yokluğu.**</span><span class="sxs-lookup"><span data-stu-id="046de-152">**Absence of Constraints.**</span></span> <span data-ttu-id="046de-153">Bir tür parametresinde herhangi bir kısıtlama belirtmezseniz, kodunuz bu tür parametresi için [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md) tarafından desteklenen işlemler ve üyelerle sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="046de-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="046de-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="046de-154">Example</span></span>

<span data-ttu-id="046de-155">Aşağıdaki örnek, sözlüğe yeni bir giriş eklemek için bir iskelet işlevi de dahil olmak üzere genel sözlük sınıfının iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="046de-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="046de-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="046de-156">Example</span></span>

<span data-ttu-id="046de-157">@No__t_0 genel olduğundan, onu kullanan kod, her biri aynı işlevselliğe sahip ancak farklı bir veri türü üzerinde işlem gören çeşitli nesneler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="046de-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="046de-158">Aşağıdaki örnek, `String` girdileri ve `Integer` anahtarlarıyla `dictionary` nesne oluşturan bir kod satırı gösterir.</span><span class="sxs-lookup"><span data-stu-id="046de-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="046de-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="046de-159">Example</span></span>

<span data-ttu-id="046de-160">Aşağıdaki örnek, önceki örnek tarafından oluşturulan eşdeğer iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="046de-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="046de-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="046de-161">See also</span></span>

- [<span data-ttu-id="046de-162">Durumunu</span><span class="sxs-lookup"><span data-stu-id="046de-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="046de-163">New İşleci</span><span class="sxs-lookup"><span data-stu-id="046de-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="046de-164">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="046de-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="046de-165">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="046de-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="046de-166">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="046de-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="046de-167">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="046de-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="046de-168">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="046de-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="046de-169">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="046de-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="046de-170">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="046de-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="046de-171">'Ndaki</span><span class="sxs-lookup"><span data-stu-id="046de-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="046de-172">Dışı</span><span class="sxs-lookup"><span data-stu-id="046de-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
