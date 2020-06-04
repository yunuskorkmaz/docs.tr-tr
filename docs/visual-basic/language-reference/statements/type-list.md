---
title: Tür Listesi
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
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412994"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="98ffb-102">Tür Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98ffb-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="98ffb-103">*Genel* programlama öğesi için *tür parametrelerini* belirtir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="98ffb-104">Birden çok parametre virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="98ffb-105">Bir tür parametresi için sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="98ffb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98ffb-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="98ffb-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="98ffb-107">Parts</span></span>

|<span data-ttu-id="98ffb-108">Terim</span><span class="sxs-lookup"><span data-stu-id="98ffb-108">Term</span></span>|<span data-ttu-id="98ffb-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="98ffb-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="98ffb-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="98ffb-110">Optional.</span></span> <span data-ttu-id="98ffb-111">Yalnızca Genel arabirimlerde ve temsilcilerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="98ffb-112">[In](../modifiers/in-generic-modifier.md) anahtar sözcüğünü kullanarak [Out](../modifiers/out-generic-modifier.md) anahtar sözcüğünü veya değişken varyantını kullanarak bir tür covaryant bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98ffb-112">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="98ffb-113">Bkz. [Kovaryans ve değişken varyansı](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="98ffb-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="98ffb-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-114">Required.</span></span> <span data-ttu-id="98ffb-115">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="98ffb-115">Name of the type parameter.</span></span> <span data-ttu-id="98ffb-116">Bu, karşılık gelen tür bağımsız değişkeni tarafından sağlanan tanımlı bir türle değiştirilmesini sağlamak için bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="98ffb-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="98ffb-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="98ffb-117">Optional.</span></span> <span data-ttu-id="98ffb-118">İçin sağlanabilecek veri türünü kısıtlayan gereksinimlerin listesi `typename` .</span><span class="sxs-lookup"><span data-stu-id="98ffb-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="98ffb-119">Birden çok kısıtlamaınız varsa bunları küme ayraçları () içine alın `{ }` ve bunları virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="98ffb-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="98ffb-120">Kısıtlama listesini [as](as-clause.md) anahtar sözcüğüyle birlikte tanıtmalısınız.</span><span class="sxs-lookup"><span data-stu-id="98ffb-120">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="98ffb-121">`As`Listenin başlangıcında yalnızca bir kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="98ffb-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98ffb-122">Remarks</span></span>

<span data-ttu-id="98ffb-123">Her genel programlama öğesi en az bir tür parametresi almalıdır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="98ffb-124">Tür parametresi, bir genel türün örneğini oluşturduğunda istemci kodunun belirttiği belirli bir tür ( *oluşturulmuş bir öğe*) için yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="98ffb-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="98ffb-125">Bir genel sınıf, yapı, arabirim, yordam veya temsilci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98ffb-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="98ffb-126">Genel bir türün ne zaman tanımlanacağı hakkında daha fazla bilgi için, bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="98ffb-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="98ffb-127">Tür parametresi adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="98ffb-127">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="98ffb-128">Kurallar</span><span class="sxs-lookup"><span data-stu-id="98ffb-128">Rules</span></span>

- <span data-ttu-id="98ffb-129">**Ayraçlar.**</span><span class="sxs-lookup"><span data-stu-id="98ffb-129">**Parentheses.**</span></span> <span data-ttu-id="98ffb-130">Bir tür parametre listesi [sağlarsanız, onu](of-clause.md) parantez içine almalısınız ve listeyi anahtar kelimesiyle birlikte almalısınız.</span><span class="sxs-lookup"><span data-stu-id="98ffb-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="98ffb-131">`Of`Listenin başlangıcında yalnızca bir kez kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="98ffb-132">**Kısıtlamaları.**</span><span class="sxs-lookup"><span data-stu-id="98ffb-132">**Constraints.**</span></span> <span data-ttu-id="98ffb-133">Bir tür parametresindeki *kısıtlamaların* listesi, aşağıdaki öğeleri herhangi bir kombinasyonda içerebilir:</span><span class="sxs-lookup"><span data-stu-id="98ffb-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="98ffb-134">Herhangi bir sayıda arabirim.</span><span class="sxs-lookup"><span data-stu-id="98ffb-134">Any number of interfaces.</span></span> <span data-ttu-id="98ffb-135">Sağlanan tür, bu listedeki her arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="98ffb-136">En fazla bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="98ffb-136">At most one class.</span></span> <span data-ttu-id="98ffb-137">Sağlanan tür bu sınıftan devralması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="98ffb-138">`New`Anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="98ffb-138">The `New` keyword.</span></span> <span data-ttu-id="98ffb-139">Sağlanan tür, genel türünün erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="98ffb-140">Bir tür parametresini bir veya daha fazla arabirim ile sınırlandırdıysanız, bu faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="98ffb-141">Arabirimleri uygulayan bir tür bir oluşturucuyu kullanıma sunmayabilir ve bir oluşturucunun erişim düzeyine bağlı olarak, genel türdeki kod buna erişemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="98ffb-142">`Class`Anahtar sözcüğü ya da `Structure` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="98ffb-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="98ffb-143">`Class`Anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir başvuru türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir String, array veya Delegate veya bir sınıftan oluşturulmuş bir nesne.</span><span class="sxs-lookup"><span data-stu-id="98ffb-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="98ffb-144">`Structure`Anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir değer türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir yapı, numaralandırma veya Öğesel veri türü.</span><span class="sxs-lookup"><span data-stu-id="98ffb-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="98ffb-145">Hem hem de `Class` aynı olamaz `Structure` `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="98ffb-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="98ffb-146">Sağlanan tür, içindeki dahil ettiğiniz her gereksinimi karşılamalıdır `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="98ffb-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="98ffb-147">Her tür parametresindeki kısıtlamalar, diğer tür parametrelerinin kısıtlamalarından bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="98ffb-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="98ffb-148">Behavior</span></span>

- <span data-ttu-id="98ffb-149">**Derleme zamanı değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="98ffb-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="98ffb-150">Genel programlama öğesinden oluşturulmuş bir tür oluşturduğunuzda, her tür parametresi için tanımlı bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="98ffb-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="98ffb-151">Visual Basic derleyici, genel öğe içindeki her oluşum için sağlanan türü kullanır `typename` .</span><span class="sxs-lookup"><span data-stu-id="98ffb-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="98ffb-152">**Kısıtlamaların yokluğu.**</span><span class="sxs-lookup"><span data-stu-id="98ffb-152">**Absence of Constraints.**</span></span> <span data-ttu-id="98ffb-153">Bir tür parametresinde herhangi bir kısıtlama belirtmezseniz, kodunuz bu tür parametresi için [nesne veri türü](../data-types/object-data-type.md) tarafından desteklenen işlemler ve üyelerle sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="98ffb-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="98ffb-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="98ffb-154">Example</span></span>

<span data-ttu-id="98ffb-155">Aşağıdaki örnek, sözlüğe yeni bir giriş eklemek için bir iskelet işlevi de dahil olmak üzere genel sözlük sınıfının iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="98ffb-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="98ffb-156">Example</span></span>

<span data-ttu-id="98ffb-157">`dictionary`Genel olduğundan, onu kullanan kod, her biri aynı işlevselliğe sahip ancak farklı bir veri türü üzerinde işlem gören çeşitli nesneler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="98ffb-158">Aşağıdaki örnek, `dictionary` girdiler ve anahtarlarla bir nesne oluşturan kod satırını gösterir `String` `Integer` .</span><span class="sxs-lookup"><span data-stu-id="98ffb-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="98ffb-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="98ffb-159">Example</span></span>

<span data-ttu-id="98ffb-160">Aşağıdaki örnek, önceki örnek tarafından oluşturulan eşdeğer iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98ffb-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="98ffb-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98ffb-161">See also</span></span>

- [<span data-ttu-id="98ffb-162">Durumunu</span><span class="sxs-lookup"><span data-stu-id="98ffb-162">Of</span></span>](of-clause.md)
- [<span data-ttu-id="98ffb-163">New Işleci</span><span class="sxs-lookup"><span data-stu-id="98ffb-163">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="98ffb-164">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="98ffb-164">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="98ffb-165">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="98ffb-165">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="98ffb-166">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="98ffb-166">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="98ffb-167">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="98ffb-167">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="98ffb-168">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="98ffb-168">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="98ffb-169">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="98ffb-169">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="98ffb-170">Kovaryans ve değişken sapması</span><span class="sxs-lookup"><span data-stu-id="98ffb-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="98ffb-171">İçinde</span><span class="sxs-lookup"><span data-stu-id="98ffb-171">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="98ffb-172">Dışı</span><span class="sxs-lookup"><span data-stu-id="98ffb-172">Out</span></span>](../modifiers/out-generic-modifier.md)
