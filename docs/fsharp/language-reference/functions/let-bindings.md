---
title: let Bağlamaları
description: "Bir tanıtıcıyı bir değer veya işlevle ilişkilendiren F # ' Let ' bağlamasını nasıl kullanacağınızı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812230"
---
# <a name="let-bindings"></a><span data-ttu-id="c043e-103">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c043e-103">let Bindings</span></span>

<span data-ttu-id="c043e-104">*Bağlama* bir tanımlayıcıyı bir değer veya işlevle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="c043e-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="c043e-105">Bir `let` adı bir değere veya işleve bağlamak için anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c043e-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="c043e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c043e-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="c043e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c043e-107">Remarks</span></span>

<span data-ttu-id="c043e-108">`let`Anahtar sözcüğü, bir veya daha fazla ad için değerleri ya da işlev değerlerini tanımlamak üzere deyimlerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c043e-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="c043e-109">İfadenin en basit formu `let` , bir adı aşağıdaki gibi basit bir değere bağlar.</span><span class="sxs-lookup"><span data-stu-id="c043e-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="c043e-110">İfadeyi yeni bir satır kullanarak tanımlayıcıdan ayırdıysanız, aşağıdaki kodda olduğu gibi, ifadenin her satırını girintileyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c043e-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="c043e-111">Yalnızca bir ad yerine, aşağıdaki kodda gösterildiği gibi, adları içeren bir model, örneğin bir tanımlama grubu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="c043e-112">*Body ifadesi* , adların kullanıldığı ifadedir.</span><span class="sxs-lookup"><span data-stu-id="c043e-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="c043e-113">Gövde ifadesi kendi satırında görünür, bu, anahtar kelimesinin ilk karakteriyle tam olarak çizgiye kadar girintilenir `let` :</span><span class="sxs-lookup"><span data-stu-id="c043e-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="c043e-114">Bir `let` bağlama modül düzeyinde, bir sınıf türünün tanımında veya bir işlev tanımında olduğu gibi yerel kapsamlarda görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="c043e-115">`let`Bir modülde veya bir sınıf türünde en üst düzeydeki bir bağlamanın gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerinde gövde ifadesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c043e-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="c043e-116">Aşağıdaki kodda gösterildiği gibi, ilişkili adlar, tanım noktası sonrasında kullanılabilir, ancak bağlama görüntülenmeden önce herhangi bir noktada kullanılamaz `let` .</span><span class="sxs-lookup"><span data-stu-id="c043e-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="c043e-117">İşlev bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c043e-117">Function Bindings</span></span>

<span data-ttu-id="c043e-118">İşlev bağlamaları, aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adını ve parametreleri içermesi dışında değer bağlamaları kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="c043e-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="c043e-119">Genel olarak parametreler, demet deseni gibi desenlerdir:</span><span class="sxs-lookup"><span data-stu-id="c043e-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="c043e-120">`let`Bağlama ifadesi, son ifadenin değerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c043e-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="c043e-121">Bu nedenle, aşağıdaki kod örneğinde değeri, `result` `100 * function3 (1, 2)` olarak değerlendirilen ' den hesaplanır `300` .</span><span class="sxs-lookup"><span data-stu-id="c043e-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="c043e-122">Daha fazla bilgi için bkz. [işlevler](index.md).</span><span class="sxs-lookup"><span data-stu-id="c043e-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="c043e-123">Tür ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="c043e-123">Type Annotations</span></span>

<span data-ttu-id="c043e-124">Parametre türlerini, iki nokta üst üste ekleyerek belirtebilirsiniz (:) sonra parantez içine alınmış bir tür adı.</span><span class="sxs-lookup"><span data-stu-id="c043e-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="c043e-125">Ayrıca, iki nokta üst üste ekleyerek ve son parametreden sonra yazarak dönüş değerinin türünü de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c043e-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="c043e-126">Tam tür ek açıklamalarını `function1` parametre türleri olarak tamsayılar ile aşağıdaki gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c043e-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="c043e-127">Açık tür parametreleri olmadığında, işlevlerin parametre türlerini belirlemekte tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c043e-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="c043e-128">Bu, genel olacak bir parametre türünün otomatik olarak genelleştirilmesi dahil olabilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="c043e-129">Daha fazla bilgi için bkz. [Otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="c043e-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="c043e-130">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c043e-130">let Bindings in Classes</span></span>

<span data-ttu-id="c043e-131">`let`Bağlama bir yapı veya kayıt türünde değil, sınıf türünde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="c043e-132">Sınıf türünde bir Let bağlaması kullanmak için, sınıfın bir birincil oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c043e-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="c043e-133">Oluşturucu parametreleri, sınıf tanımındaki tür adından sonra gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="c043e-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="c043e-134">`let`Bir sınıf türündeki bağlama, bu sınıf türü için özel alanları ve üyeleri tanımlar ve `do` türdeki bağlamalarla birlikte, türün birincil oluşturucusunun kodunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c043e-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="c043e-135">Aşağıdaki kod örneklerinde `MyClass` özel alanlar ve içeren bir sınıf gösterilmektedir `field1` `field2` .</span><span class="sxs-lookup"><span data-stu-id="c043e-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="c043e-136">Ve kapsamları, `field1` `field2` bildirildiği türle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c043e-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="c043e-137">Daha fazla bilgi için bkz. [ `let` sınıflarda](../members/let-bindings-in-classes.md) ve [sınıflarda](../classes.md)bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="c043e-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="c043e-138">Let bağlamalarında tür parametreleri</span><span class="sxs-lookup"><span data-stu-id="c043e-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="c043e-139">`let`Modül düzeyinde bir tür veya bir hesaplama ifadesinde bir bağlama açık tür parametrelerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="c043e-140">Bir ifadede, işlev tanımı içindeki gibi bir bağlamanın tür parametreleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="c043e-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="c043e-141">Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="c043e-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="c043e-142">Let bağlamalarında öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c043e-142">Attributes on let Bindings</span></span>

<span data-ttu-id="c043e-143">Öznitelikler `let` , aşağıdaki kodda gösterildiği gibi, bir modüldeki en üst düzey bağlamalar için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="c043e-144">Let bağlamalarının kapsamı ve erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="c043e-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="c043e-145">Bir Let bağlaması ile belirtilen bir varlığın kapsamı, bağlama göründükten sonra kapsayan kapsamın (bir işlev, modül, dosya veya sınıf gibi) bölümüyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c043e-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="c043e-146">Bu nedenle, bağlamanın bir ada bir ad sunmasına izin ver.</span><span class="sxs-lookup"><span data-stu-id="c043e-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="c043e-147">Bir modülde, bir modüldeki izin bağlamaları modülün ortak işlevlerine derlendiğinden, bir modüle izin ver değeri veya işlevi modülün istemcileri tarafından erişilebilirdir.</span><span class="sxs-lookup"><span data-stu-id="c043e-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="c043e-148">Buna karşılık, bir sınıftaki bağlamaların sınıfına özel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c043e-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="c043e-149">Normalde, modüller içindeki işlevler, istemci kodu tarafından kullanıldığında modülün adı ile nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c043e-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="c043e-150">Örneğin, bir modülün işlevi varsa `Module1` `function1` , kullanıcılar `Module1.function1` işlevine başvurmak için belirtecekti.</span><span class="sxs-lookup"><span data-stu-id="c043e-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="c043e-151">Modül kullanıcıları modül adı tarafından nitelendirilmeden Bu modüldeki işlevlerin kullanılabilmesini sağlamak için içeri aktarma bildirimi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c043e-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="c043e-152">Yalnızca bahsedilen örnekte, modülün kullanıcıları bu durumda içeri aktarma bildirimini aç ' ı kullanarak modülü açabilir `Module1` ve bundan sonra doğrudan öğesine başvurabilirler `function1` .</span><span class="sxs-lookup"><span data-stu-id="c043e-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="c043e-153">Bazı modüllerin [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)özniteliği vardır. Bu, sergiledikleri işlevlerin modülün adı ile nitelendirilmeleri gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c043e-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="c043e-154">Örneğin, F # liste modülünün bu özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="c043e-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="c043e-155">Modüller ve erişim denetimi hakkında daha fazla bilgi için bkz. [modüller](../modules.md) ve [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="c043e-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c043e-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c043e-156">See also</span></span>

- [<span data-ttu-id="c043e-157">İşlevler</span><span class="sxs-lookup"><span data-stu-id="c043e-157">Functions</span></span>](index.md)
- [<span data-ttu-id="c043e-158">`let` Sınıflarda bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c043e-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
