---
title: Tür Çıkarma
description: Bilgi nasıl F# derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini algılar.
ms.date: 05/16/2016
ms.openlocfilehash: 3e61d5c81fde0a48af66a47745123a842dc04cb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666241"
---
# <a name="type-inference"></a><span data-ttu-id="ab9a6-103">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="ab9a6-103">Type Inference</span></span>

<span data-ttu-id="ab9a6-104">Bu konu açıklar nasıl F# derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini algılar.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="ab9a6-105">Genel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="ab9a6-105">Type Inference in General</span></span>

<span data-ttu-id="ab9a6-106">Türlerini belirtmek gerekmez tür çıkarımı fikirdir F# yapıları hariç, derleyicinin türü yaratacağı çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="ab9a6-107">Açık tür bilgileri atlama gelmez, F# dinamik olarak yazılmış bir dildir veya bu değerleri F# zayıf sahipli olan türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="ab9a6-108">F#Derleyici, derleme sırasında her yapı için tam bir tür çıkarır anlamına gelen bir statik olarak belirlenmiş, dilidir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="ab9a6-109">Her yapı türlerini kullanarak derleyicinin için yeterli bilgi değilse açık tür ek açıklamaları yere kod ekleyerek ek tür bilgileri, genellikle sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="ab9a6-110">Çıkarım parametre ve dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="ab9a6-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="ab9a6-111">Bir parametre listesinde her parametresinin türünü belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="ab9a6-112">Ve henüz F# statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="ab9a6-113">Türlerine her zaman açık belirtmeyin bağlamına dayalı türü derleyicinin çıkarır.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="ab9a6-114">Belirtilen tür Aksi durumda değilse, genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="ab9a6-115">Kod bir değer tutarsız kullanıyorsa, şekilde olduğunu Hayır tek bir değerin tüm kullanımları derleyici bir hata bildiriyor karşılayan türün gösterilmesi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="ab9a6-116">Bir işlevin dönüş türü işlevdeki son ifadenin türü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="ab9a6-117">Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü tüm çıkarılan olmasını `int` çünkü değişmez değer `100` türünde `int`.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="ab9a6-118">Tür çıkarımı değişmez değerleri değiştirerek etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="ab9a6-119">Siz `100` bir `uint32` soneki ekleyerek `u`, türlerini `a`, `b`, ve dönüş değeri olarak ortaya çıkan `uint32`.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="ab9a6-120">Ayrıca etkileyebilir çıkarımı işlevleri ve yalnızca belirli bir tür ile çalışan yöntemleri gibi tür kısıtlamalar yaptığından diğer yapıları kullanarak yazın.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="ab9a6-121">Ayrıca, açık bir tür ek açıklamaları, ifadelerdeki değişkenler veya işlev veya metot parametreleri aşağıdaki örneklerde gösterildiği gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="ab9a6-122">Farklı kısıtlamaları arasında çakışma olursa, hatalara neden.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="ab9a6-123">Ayrıca, bir tür ek açıklamasına tüm parametreleri sağlayarak bir işlevin dönüş değeri de açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="ab9a6-124">Bir tür ek açıklamasına parametre üzerinde kullanışlı olduğu bir yaygın parametresi bir nesne türü ve üye kullanmak istediğiniz bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="ab9a6-125">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="ab9a6-125">Automatic Generalization</span></span>

<span data-ttu-id="ab9a6-126">İşlev kodu bir parametre türüne bağımlı değilse, derleyici genel parametre olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="ab9a6-127">Bu adlandırılır *otomatik Genelleştirme*, ve genel kod karmaşıklığı artırmadan yazma için güçlü bir yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="ab9a6-128">Örneğin, aşağıdaki işlev bir demet içinde herhangi bir türde iki parametre birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="ab9a6-129">Türün olacak şekilde gösterilmesi</span><span class="sxs-lookup"><span data-stu-id="ab9a6-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="ab9a6-130">Ek Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ab9a6-130">Additional Information</span></span>

<span data-ttu-id="ab9a6-131">Tür çıkarımı daha ayrıntılı olarak açıklanan F# dil belirtimi.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab9a6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab9a6-132">See also</span></span>

- [<span data-ttu-id="ab9a6-133">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="ab9a6-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)