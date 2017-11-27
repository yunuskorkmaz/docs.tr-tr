---
title: "let Bağlamaları (F#)"
description: "F # 'bir değer veya işlevi bir tanımlayıcı ilişkilendirir bağlama let' kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a><span data-ttu-id="24b72-104">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-104">let Bindings</span></span>

<span data-ttu-id="24b72-105">A *bağlama* bir değer veya işlevi bir tanımlayıcı ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="24b72-105">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="24b72-106">Kullandığınız `let` bir değer veya işlevi için bir ad bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="24b72-106">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="24b72-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24b72-107">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="24b72-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24b72-108">Remarks</span></span>

<span data-ttu-id="24b72-109">`let` Anahtar sözcüğü değerleri veya bir veya daha fazla adları için işlevi değerleri tanımlamak için ifadeleri bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24b72-109">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="24b72-110">En basit biçimi `let` ifadesi bir ad gibi basit bir değere bağlar.</span><span class="sxs-lookup"><span data-stu-id="24b72-110">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="24b72-111">Yeni bir satır kullanarak tanımlayıcı ifadesinden ayırmak, her satırın aşağıdaki kodu olduğu gibi ifadesinin girinti gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b72-111">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="24b72-112">Yalnızca bir adı yerine, adlarını içeren bir desen belirtilebilir, aşağıdaki kodda gösterildiği gibi bir tanımlama grubu,.</span><span class="sxs-lookup"><span data-stu-id="24b72-112">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="24b72-113">*Gövde ifade* adları kullanılır ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="24b72-113">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="24b72-114">Gövde ifade ilk karakteri ile tam olarak yukarı satırına girintili kendi satırında görünen `let` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="24b72-114">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="24b72-115">A `let` bağlama görünebilir modülü düzeyinde bir sınıf türü tanımını veya yerel kapsamlar, işlev tanımının olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="24b72-115">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="24b72-116">A `let` bağlama en üst düzeydeki bir modüle ya da bir sınıf türü bir gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerde gövde ifade gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24b72-116">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="24b72-117">Bağımlı adları, tanımının, ancak önce herhangi bir noktada değil noktadan sonra kullanılabilir `let` aşağıdaki kodda gösterildiği gibi bağlama görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24b72-117">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a><span data-ttu-id="24b72-118">İşlev bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-118">Function Bindings</span></span>

<span data-ttu-id="24b72-119">Aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adı ve parametreleri dahil dışında işlev bağlamaları değeri bağlamaları için kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="24b72-119">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="24b72-120">Genel olarak, bir demet deseni gibi düzenleri Parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24b72-120">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="24b72-121">A `let` ifade bağlama son deyim değerine değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="24b72-121">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="24b72-122">Bu nedenle, aşağıdaki kod örneğinde, değeri içinde `result` gelen hesaplanan `100 * function3 (1, 2)`, hesaplar için `300`.</span><span class="sxs-lookup"><span data-stu-id="24b72-122">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="24b72-123">Daha fazla bilgi için bkz: [işlevler](index.md).</span><span class="sxs-lookup"><span data-stu-id="24b72-123">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="24b72-124">Tür ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-124">Type Annotations</span></span>

<span data-ttu-id="24b72-125">Parantez içinde tüm iliştirilmiş bir tür adı ve ardından iki nokta (:) dahil ederek parametreler için türlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b72-125">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="24b72-126">Dönüş değeri türü iki nokta üst üste ve türünü sonra son parametre ekleyerek de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b72-126">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="24b72-127">Tam tür ek açıklamaları için `function1`, parametre türleri olarak tamsayılar ile aşağıdaki gibi olur.</span><span class="sxs-lookup"><span data-stu-id="24b72-127">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="24b72-128">Açık tür parametre bulunmadığında tür çıkarımı işlevlerin parametre türlerini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24b72-128">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="24b72-129">Bu, otomatik olarak genel olarak bir parametrenin türü genelleme içerebilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-129">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="24b72-130">Daha fazla bilgi için bkz: [otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="24b72-130">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="24b72-131">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-131">let Bindings in Classes</span></span>

<span data-ttu-id="24b72-132">A `let` bağlama, sınıf türü ancak yapısı veya kayıt türü görünebilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-132">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="24b72-133">Bir sınıf türü bağlama let kullanmak için sınıfı birincil bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24b72-133">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="24b72-134">Oluşturucu parametreleri sınıf tanımında tür adından sonra görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b72-134">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="24b72-135">A `let` bir sınıf türü bağlamasında tanımlar özel alanlar ve üyeleri bu sınıf türü için ve ile birlikte `do` türü bağlama türü için birincil Oluşturucu için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24b72-135">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="24b72-136">Bir sınıfa aşağıdaki kodu örnekler `MyClass` özel alanlarla `field1` ve `field2`.</span><span class="sxs-lookup"><span data-stu-id="24b72-136">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="24b72-137">Kapsamların `field1` ve `field2` bunlar bildirilen türü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="24b72-137">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="24b72-138">Daha fazla bilgi için bkz: [ `let` sınıflardaki bağlamaları](../members/let-bindings-in-classes.md) ve [sınıfları](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="24b72-138">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="24b72-139">Tür parametrelerinde let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-139">Type Parameters in let Bindings</span></span>

<span data-ttu-id="24b72-140">A `let` bağlama düzeyinde modülü, bir tür ya da bir hesaplama ifadesi açık türü parametrelerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-140">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="24b72-141">Bir işlev tanımı içinde gibi bir ifadede bağlama let tür parametreleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="24b72-141">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="24b72-142">Daha fazla bilgi için bkz: [genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="24b72-142">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="24b72-143">Özniteliklerde let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-143">Attributes on let Bindings</span></span>

<span data-ttu-id="24b72-144">Öznitelikleri uygulanabilir çok üst düzey `let` aşağıdaki kodda gösterildiği gibi bir modüldeki bağlar.</span><span class="sxs-lookup"><span data-stu-id="24b72-144">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="24b72-145">Kapsam ve Let bağlamaları erişilebilirliğini</span><span class="sxs-lookup"><span data-stu-id="24b72-145">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="24b72-146">Let bağlama ile bildirilen varlık kapsamı içeren bölümüne sınırlıdır kapsam (bir işlev, modül, dosya veya sınıf gibi) bağlama göründükten sonra.</span><span class="sxs-lookup"><span data-stu-id="24b72-146">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="24b72-147">Bu nedenle, bir let bağlama kapsam içine bir ad tanıtır söylenebilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-147">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="24b72-148">Bir modül let bağlamaları modülünün genel işlevlerini derlenen beri modülü erişilebilen sürece bir modüldeki bir let ilişkili değer veya işlevi bir modül istemcilere erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-148">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="24b72-149">Bunun aksine, bir sınıf let bağlamaları sınıfına özeldir.</span><span class="sxs-lookup"><span data-stu-id="24b72-149">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="24b72-150">Normalde, modüllerdeki işlevlerin istemci kodu tarafından kullanıldığında, modülün adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="24b72-150">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="24b72-151">Örneğin, bir modül, `Module1` bir işlev `function1`, kullanıcıların belirtirsiniz `Module1.function1` işlevine başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="24b72-151">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="24b72-152">Kullanıcılar bir modülün modül adı tarafından yetkili olmadan bu modül içinde işlevleri kullanmak için kullanılabilir hale getirmek alma bildirimi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="24b72-152">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="24b72-153">Yalnızca belirtilen örnekte modülü kullanıcılarının bu durumda modül alma bildirimi açık kullanarak açabilirsiniz `Module1` ve bundan sonra başvurulacak `function1` doğrudan.</span><span class="sxs-lookup"><span data-stu-id="24b72-153">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="24b72-154">Bazı modüller özniteliğine sahip [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), yani ortaya işlevleri modülünün adıyla nitelendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b72-154">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="24b72-155">Örneğin, F # List Modülü bu özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="24b72-155">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="24b72-156">Modülleri ve erişim denetimi hakkında daha fazla bilgi için bkz: [modülleri](../modules.md) ve [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="24b72-156">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24b72-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24b72-157">See Also</span></span>

[<span data-ttu-id="24b72-158">İşlevler</span><span class="sxs-lookup"><span data-stu-id="24b72-158">Functions</span></span>](index.md)

[<span data-ttu-id="24b72-159">`let`Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="24b72-159">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
