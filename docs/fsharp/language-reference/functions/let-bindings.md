---
title: let Bağlamaları (F#)
description: F# 'let bir değer ya da işlevin tanımlayıcı ilişkilendiren bir bağlama' kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 1a35b5a39f2768a18665b5c7fe768af0e7714577
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43777476"
---
# <a name="let-bindings"></a><span data-ttu-id="a08ec-103">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-103">let Bindings</span></span>

<span data-ttu-id="a08ec-104">A *bağlama* bir değer ya da işlevin tanımlayıcı ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="a08ec-105">Kullandığınız `let` bir değer veya işlevi için bir ad bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a08ec-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="a08ec-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a08ec-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="a08ec-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a08ec-107">Remarks</span></span>

<span data-ttu-id="a08ec-108">`let` Anahtar sözcüğü, bağlama ifadeleri değerleri veya bir veya daha çok işlevi değerlerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="a08ec-109">En basit biçimi `let` ifade bir ad gibi basit bir değere bağlar.</span><span class="sxs-lookup"><span data-stu-id="a08ec-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="a08ec-110">Yeni bir satır kullanarak tanımlayıcı ifadesinden ayırarak, aşağıdaki kodda gösterildiği gibi ifadesinin her satırı girintile gerekir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="a08ec-111">Bir ad yerine yalnızca, adları içeren bir desen belirtilebilir, aşağıdaki kodda gösterildiği gibi bir tanımlama.</span><span class="sxs-lookup"><span data-stu-id="a08ec-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="a08ec-112">*Gövde ifadesi* ifade adları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="a08ec-113">Gövde ifadesi ilk karakteri ile tam olarak ayarlamak için satır girintili kendi satırında görünür `let` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="a08ec-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="a08ec-114">A `let` bağlama görünebilir Modül düzeyinde bir sınıf türünün tanımında veya yerel kapsamlar, bir işlev tanımı gibi.</span><span class="sxs-lookup"><span data-stu-id="a08ec-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="a08ec-115">A `let` bağlama en üst düzeyinde bir modül veya sınıf türünde bir gövde ifadesi olması gerekmez, ancak diğer kapsam düzeylerinde gövde ifadesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="a08ec-116">Bağımlı adlar, tanımı, ancak önce herhangi bir noktada değil noktadan sonra kullanılabilir `let` aşağıdaki kodda gösterildiği gibi bağlama görünür.</span><span class="sxs-lookup"><span data-stu-id="a08ec-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="a08ec-117">İşlev bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-117">Function Bindings</span></span>

<span data-ttu-id="a08ec-118">Aşağıdaki kodda gösterildiği gibi işlev bağlamaları işlev adı ve parametreler dahil dışında işlev bağlamaları değeri bağlamaları için kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="a08ec-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="a08ec-119">Genel olarak, bir kayıt düzeni deseni gibi kalıplar Parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a08ec-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="a08ec-120">A `let` ifade bağlama değeri son ifade olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="a08ec-121">Bu nedenle, aşağıdaki kod örneği, değeri içinde `result` gelen hesaplanan `100 * function3 (1, 2)`, hangi değerlendirir `300`.</span><span class="sxs-lookup"><span data-stu-id="a08ec-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="a08ec-122">Daha fazla bilgi için [işlevleri](index.md).</span><span class="sxs-lookup"><span data-stu-id="a08ec-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="a08ec-123">Tür ek açıklamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-123">Type Annotations</span></span>

<span data-ttu-id="a08ec-124">Tür parametreleri için parantez içinde tüm kapalı bir tür adını ardından bir iki nokta üst üste (:) dahil ederek belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08ec-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="a08ec-125">Dönüş değerinin türü iki nokta üst üste ve türdeki sonra son parametre ekleyerek de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08ec-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="a08ec-126">İçin tam bir tür ek açıklamalar `function1`, parametre türleri olarak tamsayı ile şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="a08ec-127">Açık tür parametre bulunmadığında tür çıkarımı işlevlerin parametre türlerini belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="a08ec-128">Bu, otomatik olarak genel bir parametre türü genelleştiriliyor içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="a08ec-129">Daha fazla bilgi için [otomatik Genelleştirme](../generics/automatic-generalization.md) ve [tür çıkarımı](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a08ec-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="a08ec-130">Sınıflardaki let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-130">let Bindings in Classes</span></span>

<span data-ttu-id="a08ec-131">A `let` bağlama, sınıf türünde ancak yapısı veya kayıt türü görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="a08ec-132">Sınıfı, bir sınıf türünde bağlama bir let kullanmak için bir birincil oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="a08ec-133">Oluşturucu parametresi, sınıf tanımında tür adından sonra yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="a08ec-134">A `let` özel alanlar ve üyeleri sınıf türüne ve ile birlikte bir sınıf türü bağlamasında tanımlar `do` türündeki bağlama türü için birincil Oluşturucu için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a08ec-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="a08ec-135">Aşağıdaki kod örnekleri, bir sınıf Göster `MyClass` özel alanlara sahip `field1` ve `field2`.</span><span class="sxs-lookup"><span data-stu-id="a08ec-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="a08ec-136">Kapsamlar `field1` ve `field2` içinde bildirilen türü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="a08ec-137">Daha fazla bilgi için [ `let` sınıflardaki bağlamaları](../members/let-bindings-in-classes.md) ve [sınıfları](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="a08ec-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="a08ec-138">Tür parametrelerinde let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="a08ec-139">A `let` bağlama Modül düzeyinde bir türü veya bir hesaplama ifadesi açık tür parametrelerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="a08ec-140">Bir işlev tanımı içinde bağlama gibi bir ifadede bir let Tür parametrelerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="a08ec-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="a08ec-141">Daha fazla bilgi için [genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="a08ec-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="a08ec-142">Özniteliklerinde let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-142">Attributes on let Bindings</span></span>

<span data-ttu-id="a08ec-143">Öznitelikleri uygulanabilir çok en üst düzey `let` bağlamaları aşağıdaki kodda gösterildiği gibi bir modülde.</span><span class="sxs-lookup"><span data-stu-id="a08ec-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="a08ec-144">Kapsamı ve erişilebilirliğini Let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="a08ec-145">Let bağlama ile bildirilen bir varlığa kapsamını içeren kısmı sınırlıdır kapsamını (bir işlev, modül, dosya veya sınıf gibi) bağlama göründükten sonra.</span><span class="sxs-lookup"><span data-stu-id="a08ec-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="a08ec-146">Bu nedenle, let bağlama bir kapsamın içine bir ad tanıtır söylenebilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="a08ec-147">Let bağlamaları modülünde modülünün genel işlevlere derlenmiş modülü erişilebilir olduğu sürece bir modülde let ilişkili değer veya işlevi bir modül istemcilere erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="a08ec-148">Aksine, sınıfa bir sınıfta let bağlamaları özeldir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="a08ec-149">Normalde, modüllerdeki İşlevler, istemci kodu tarafından kullanıldığında modülünün adı ile nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="a08ec-150">Örneğin, bir modül, `Module1` bir işlev `function1`, kullanıcıların belirtirsiniz `Module1.function1` işleve başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="a08ec-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="a08ec-151">Bir modülün kullanıcılar, içeri aktarma bildirimi, modül adı tarafından yetkili olmadan bu modülündeki işlevleri kullanmak için kullanılabilir hale getirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="a08ec-152">Yalnızca bahsedilen örnekte, modülün kullanıcılar bu durumda modül içeri aktarma bildirimi açık kullanarak açabilirsiniz `Module1` ve bundan sonra başvurmak `function1` doğrudan.</span><span class="sxs-lookup"><span data-stu-id="a08ec-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="a08ec-153">Bazı modüller özniteliğine sahip [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), yani ortaya işlevleri modül adı ile nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a08ec-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="a08ec-154">Örneğin, F# List Modülü, bu öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="a08ec-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="a08ec-155">Modüller ve erişim denetimi hakkında daha fazla bilgi için bkz. [modülleri](../modules.md) ve [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="a08ec-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a08ec-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a08ec-156">See also</span></span>

- [<span data-ttu-id="a08ec-157">İşlevler</span><span class="sxs-lookup"><span data-stu-id="a08ec-157">Functions</span></span>](index.md)
- [<span data-ttu-id="a08ec-158">`let` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="a08ec-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
