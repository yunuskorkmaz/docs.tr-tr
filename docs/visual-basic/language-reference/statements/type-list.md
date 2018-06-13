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
ms.openlocfilehash: 5fbb07154fce27feb257b431c1726446b42fbfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605296"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="7f5a2-102">Tür Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f5a2-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="7f5a2-103">Belirtir *tür parametrelerindeki* için bir *genel* programlama öğesidir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="7f5a2-104">Birden çok parametre virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="7f5a2-105">Aşağıdaki bir tür parametresi sözdizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5a2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f5a2-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="7f5a2-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7f5a2-107">Parts</span></span>  
  
|<span data-ttu-id="7f5a2-108">Terim</span><span class="sxs-lookup"><span data-stu-id="7f5a2-108">Term</span></span>|<span data-ttu-id="7f5a2-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="7f5a2-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="7f5a2-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-110">Optional.</span></span> <span data-ttu-id="7f5a2-111">Yalnızca genel arabirimler ve temsilciler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="7f5a2-112">Kullanarak, bir tür eşdeğişken bildirebilirsiniz [çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) anahtar sözcüğü veya kullanarak karşıtı [içinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="7f5a2-113">Bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f5a2-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="7f5a2-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-114">Required.</span></span> <span data-ttu-id="7f5a2-115">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-115">Name of the type parameter.</span></span> <span data-ttu-id="7f5a2-116">Karşılık gelen tür bağımsız değişkeni tarafından sağlanan tanımlanmış bir türü değiştirilmesi için bir yer tutucu budur.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="7f5a2-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-117">Optional.</span></span> <span data-ttu-id="7f5a2-118">İçin sağlanan veri türü sınırlamak gereksinimlerinin listesi `typename`.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="7f5a2-119">Birden çok kısıtlama varsa, bunları süslü ayraçlar içinde alın (`{ }`) ve virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="7f5a2-120">Kısıtlama listesiyle tanıtmak [olarak](../../../visual-basic/language-reference/statements/as-clause.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="7f5a2-121">Kullandığınız `As` listenin başında yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f5a2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f5a2-122">Remarks</span></span>  
 <span data-ttu-id="7f5a2-123">Her genel programlama öğesi en az bir tür parametre alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="7f5a2-124">Tür parametresi belirli bir tür için bir yer tutucudur (bir *yapılandırılmış öğe*) istemci kodu genel türü örneğini oluşturduğunda belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="7f5a2-125">Genel bir sınıf tanımlama, yapısı, yordam, arabirim veya temsilci.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="7f5a2-126">Ne zaman genel tür tanımlama hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="7f5a2-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="7f5a2-127">Tür parametresi adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7f5a2-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7f5a2-128">Kurallar</span><span class="sxs-lookup"><span data-stu-id="7f5a2-128">Rules</span></span>  
  
-   <span data-ttu-id="7f5a2-129">**Parantez.**</span><span class="sxs-lookup"><span data-stu-id="7f5a2-129">**Parentheses.**</span></span> <span data-ttu-id="7f5a2-130">Tür parametre listesi sağlayın, parantez içine almanız gerekir ve listesiyle tanıtmak [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="7f5a2-131">Kullandığınız `Of` listenin başında yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="7f5a2-132">**Kısıtlamaları.**</span><span class="sxs-lookup"><span data-stu-id="7f5a2-132">**Constraints.**</span></span> <span data-ttu-id="7f5a2-133">Listesini *kısıtlamaları* türde bir parametre aşağıdaki öğeler herhangi bir bileşimini içerebilir:</span><span class="sxs-lookup"><span data-stu-id="7f5a2-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="7f5a2-134">Herhangi bir sayı arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-134">Any number of interfaces.</span></span> <span data-ttu-id="7f5a2-135">Sağlanan tür bu listede her arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="7f5a2-136">En çok bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-136">At most one class.</span></span> <span data-ttu-id="7f5a2-137">Sağlanan tür, bu sınıftan devralınan gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="7f5a2-138">`New` Anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-138">The `New` keyword.</span></span> <span data-ttu-id="7f5a2-139">Sağlanan tür genel tür erişebilirsiniz parametresiz bir kurucusu kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="7f5a2-140">Bu tür parametresi bir veya daha fazla arabirim tarafından sınırlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="7f5a2-141">Arabirimleri uygulayan bir tür bir oluşturucu kullanıma sunmuyor ve bir oluşturucu erişim düzeyine bağlı olarak, genel tür içindeki kod erişmek kuramamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="7f5a2-142">Her iki `Class` anahtar sözcüğü veya `Structure` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="7f5a2-143">`Class` Anahtar sözcüğü bir genel tür parametresi kendisine geçirilen her tür bağımsız değişkeni bir başvuru türü, örneğin bir dize, dizi veya temsilci olması veya bir nesne öğesinden bir sınıf oluşturulan gerektirecek şekilde kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="7f5a2-144">`Structure` Anahtar sözcüğü, örneğin bir yapısı, numaralandırma veya başlangıç veri türü kendisine geçirilen her tür bağımsız değişkeni bir değer türü olmasını gerektirecek şekilde bir genel tür parametresi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="7f5a2-145">Her ikisini birden içeremez `Class` ve `Structure` aynı `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="7f5a2-146">Sağlanan tür, dahil her gereksinimi karşılamak gerekir `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="7f5a2-147">Her tür parametresi kısıtlamaları diğer tür parametrelerindeki kısıtlamalar bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7f5a2-148">Davranış</span><span class="sxs-lookup"><span data-stu-id="7f5a2-148">Behavior</span></span>  
  
-   <span data-ttu-id="7f5a2-149">**Derleme zamanı değiştirme.**</span><span class="sxs-lookup"><span data-stu-id="7f5a2-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="7f5a2-150">Bir genel programlama öğesinden oluşturulan türü oluşturduğunuzda, her tür parametresi için tanımlanmış bir türü sağlayın.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="7f5a2-151">Visual Basic derleyici her oluşumu için sağlanan bu tür değiştirir `typename` genel öğesi içinde.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="7f5a2-152">**Kısıtlamaları olmayışı.**</span><span class="sxs-lookup"><span data-stu-id="7f5a2-152">**Absence of Constraints.**</span></span> <span data-ttu-id="7f5a2-153">Herhangi bir tür parametresi kısıtlamalar belirtmezseniz, kodunuzu işlemleri ve üyeleri tarafından desteklenen sınırlıdır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md) bu tür parametresi için.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f5a2-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f5a2-154">Example</span></span>  
 <span data-ttu-id="7f5a2-155">Aşağıdaki örnek sözlüğe yeni bir giriş eklemek için bir çatı işlevi dahil olmak üzere bir genel dictionary sınıfı iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7f5a2-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f5a2-156">Example</span></span>  
 <span data-ttu-id="7f5a2-157">Çünkü `dictionary` olan genel, bunu kullanan kodu çeşitli nesneleri, her aynı işlevselliğe sahip ancak farklı bir veri türü üzerinde hareket oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="7f5a2-158">Aşağıdaki örnek, bir oluşturur kod satırı gösterir bir `dictionary` nesnesi ile `String` girişleri ve `Integer` anahtarları.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7f5a2-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f5a2-159">Example</span></span>  
 <span data-ttu-id="7f5a2-160">Aşağıdaki örnek önceki örnek tarafından oluşturulan eşdeğer iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7f5a2-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f5a2-161">See Also</span></span>  
 [<span data-ttu-id="7f5a2-162">,</span><span class="sxs-lookup"><span data-stu-id="7f5a2-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="7f5a2-163">New İşleci</span><span class="sxs-lookup"><span data-stu-id="7f5a2-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="7f5a2-164">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="7f5a2-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="7f5a2-165">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7f5a2-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="7f5a2-166">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f5a2-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="7f5a2-167">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f5a2-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="7f5a2-168">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f5a2-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="7f5a2-169">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="7f5a2-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="7f5a2-170">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="7f5a2-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="7f5a2-171">İçinde</span><span class="sxs-lookup"><span data-stu-id="7f5a2-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="7f5a2-172">Çıkışı</span><span class="sxs-lookup"><span data-stu-id="7f5a2-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
