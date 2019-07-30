---
title: 'Kaynak yönetimi: Use anahtar sözcüğü'
description: Kaynak başlatma ve F# serbest bırakma işlevlerini denetleyebilen ' Use ' anahtar sözcüğü ve ' Using ' işlevi hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627264"
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="f550d-103">Kaynak yönetimi: Use anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f550d-103">Resource Management: The use Keyword</span></span>

<span data-ttu-id="f550d-104">Bu konuda, kaynak başlatma `use` ve serbest `using` bırakma işlevlerini denetleyebilen anahtar sözcüğü ve işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f550d-104">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="f550d-105">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f550d-105">Resources</span></span>

<span data-ttu-id="f550d-106">*Kaynak* terimi birden çok şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f550d-106">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="f550d-107">Evet, kaynaklar, bir uygulamanın kullandığı dizeler, grafikler ve gibi veriler olabilir, ancak bu bağlamda *kaynaklar* , grafik cihaz bağlamları, dosya tanıtıcıları, ağ ve veritabanı gibi yazılım veya işletim sistemi kaynaklarına başvurur bağlantılar, bekleme tutamaçları gibi eşzamanlılık nesneleri vb.</span><span class="sxs-lookup"><span data-stu-id="f550d-107">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="f550d-108">Bu kaynakların uygulamalar tarafından kullanılması, kaynağın işletim sisteminden veya diğer kaynak sağlayıcısından alınması ve daha sonra kaynağın başka bir uygulamaya sağlanması için havuza daha sonraki bir sürümü ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f550d-108">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="f550d-109">Uygulamalar, kaynakları ortak havuza geri bırakmayan sorunlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="f550d-109">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="f550d-110">Kaynakları yönetme</span><span class="sxs-lookup"><span data-stu-id="f550d-110">Managing Resources</span></span>

<span data-ttu-id="f550d-111">Bir uygulamadaki kaynakları verimli ve sorumlu bir şekilde yönetmek için kaynakları hemen ve öngörülebilir bir şekilde serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f550d-111">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="f550d-112">.NET Framework, `System.IDisposable` arabirimi sağlayarak bunu yapmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f550d-112">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="f550d-113">Uygulayan `System.IDisposable` bir tür, kaynakları doğru `System.IDisposable.Dispose` bir şekilde serbest bırakma yöntemine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f550d-113">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="f550d-114">İyi yazılmış uygulamalar, sınırlı bir `System.IDisposable.Dispose` kaynağı tutan herhangi bir nesne artık gerekli olmadığında hemen olarak adlandırılan garantisi verir.</span><span class="sxs-lookup"><span data-stu-id="f550d-114">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="f550d-115">Neyse ki .NET dillerinin çoğu daha kolay hale getirmek için destek sağlar ve F# özel durum yoktur.</span><span class="sxs-lookup"><span data-stu-id="f550d-115">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="f550d-116">Dispose modelini destekleyen iki yararlı dil yapıları vardır: `use` Binding `using` ve function.</span><span class="sxs-lookup"><span data-stu-id="f550d-116">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="f550d-117">Bağlamayı kullan</span><span class="sxs-lookup"><span data-stu-id="f550d-117">use Binding</span></span>

<span data-ttu-id="f550d-118">Anahtar sözcüğünün `let` bağlamakla benzer bir formu vardır: `use`</span><span class="sxs-lookup"><span data-stu-id="f550d-118">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="f550d-119">*değer* = *ifadesini* kullan</span><span class="sxs-lookup"><span data-stu-id="f550d-119">use *value* = *expression*</span></span>

<span data-ttu-id="f550d-120">`let` Bağlama ile aynı işlevselliği sağlar, ancak değer kapsam dışına geçtiğinde değere bir `Dispose` çağrı ekler.</span><span class="sxs-lookup"><span data-stu-id="f550d-120">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="f550d-121">Derleyicinin değer üzerinde null bir denetim eklediğinden, değeri ise `null`, `Dispose` çağrısının denenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f550d-121">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="f550d-122">Aşağıdaki örnek, `use` anahtar sözcüğü kullanılarak bir dosyanın otomatik olarak nasıl kapatılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f550d-122">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> <span data-ttu-id="f550d-123">Hesaplama ifadelerinde kullanabilirsiniz `use` , bu durumda `use` ifadenin özelleştirilmiş bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f550d-123">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="f550d-124">Daha fazla bilgi için bkz. [diziler](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [Hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f550d-124">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="using-function"></a><span data-ttu-id="f550d-125">Using Işlevi</span><span class="sxs-lookup"><span data-stu-id="f550d-125">using Function</span></span>

<span data-ttu-id="f550d-126">`using` İşlevi aşağıdaki biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="f550d-126">The `using` function has the following form:</span></span>

<span data-ttu-id="f550d-127">`using`(*İfade1*) *işlev veya-lambda*</span><span class="sxs-lookup"><span data-stu-id="f550d-127">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="f550d-128">Bir `using` ifadede *İfade1* , atılmalıdır olması gereken nesneyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f550d-128">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="f550d-129">*İfade1* (atılması gereken nesne) sonucu, tarafından *oluşturulan değerle eşleşen bir türün bir kalan bağımsız değişkenini bekleyen bir işlev olan Function veya-lambda öğesine bir bağımsız değişken, değer olur. İfade1*veya bu tür bir bağımsız değişken bekleyen bir lambda ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f550d-129">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="f550d-130">İşlevi yürütmenin sonunda, çalışma zamanı kaynakları çağırır `Dispose` ve serbest bırakır (değer olmadığı `null`takdirde, Dispose çağrısı denenmez).</span><span class="sxs-lookup"><span data-stu-id="f550d-130">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="f550d-131">Aşağıdaki örnek, bir Lambda `using` ifadesi ile ifadeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f550d-131">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="f550d-132">Sonraki örnekte, `using` ifadesi bir işlev ile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f550d-132">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="f550d-133">İşlevin, zaten uygulanmış bazı bağımsız değişkenlerin bulunduğu bir işlev olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f550d-133">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="f550d-134">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f550d-134">The following code example demonstrates this.</span></span> <span data-ttu-id="f550d-135">Dizeyi `XYZ`içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f550d-135">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="f550d-136">`using` İşlevi`use` ve bağlama, aynı şeyi gerçekleştirmenin neredeyse denk bir yollardır.</span><span class="sxs-lookup"><span data-stu-id="f550d-136">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="f550d-137">Anahtar sözcüğü çağrıldığında daha fazla denetim `Dispose` sağlar. `using`</span><span class="sxs-lookup"><span data-stu-id="f550d-137">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="f550d-138">Kullandığınızda `using`, `Dispose` işlevin veya lambda ifadesinin sonunda çağrılır `use` ; anahtar sözcüğünü kullandığınızda, `Dispose` kapsayan kod bloğunun sonunda çağırılır.</span><span class="sxs-lookup"><span data-stu-id="f550d-138">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="f550d-139">Genel olarak, `use` `using` işlevi yerine kullanmayı tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f550d-139">In general, you should prefer to use `use` instead of the `using` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="f550d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f550d-140">See also</span></span>

- [<span data-ttu-id="f550d-141">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f550d-141">F# Language Reference</span></span>](index.md)
