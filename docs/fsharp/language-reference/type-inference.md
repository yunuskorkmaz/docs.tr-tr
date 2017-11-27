---
title: "Tür Çıkarma (F#)"
description: "F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2d5fa4b1-732a-4d71-a62d-07f7ee79fe06
ms.openlocfilehash: c23954c0a0828cc7d2aae0553d37d5ee1dfbe152
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="type-inference"></a><span data-ttu-id="8f78d-104">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="8f78d-104">Type Inference</span></span>

<span data-ttu-id="8f78d-105">Bu konu, F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f78d-105">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="8f78d-106">Genel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="8f78d-106">Type Inference in General</span></span>
<span data-ttu-id="8f78d-107">Tür çıkarımı fikri zaman derleyici conclusively türünü türetme edilemez dışında F # yapılarını türlerini belirtmek gerekmez değildir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-107">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="8f78d-108">Açık tür bilgileri atlama F # dinamik olarak yazılan bir dil olan veya değerleri F # zayıf yazılmış anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="8f78d-108">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="8f78d-109">F # derleyici derleme sırasında her bir yapı için tam bir türe deduces anlamına gelen bir statik olarak belirtilmiş, dilidir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-109">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="8f78d-110">Her yapı türleri türetme derleyici için yeterli bilgi değilse açık tür ek açıklama herhangi bir yerde kodda ekleyerek ek tür bilgileri, genellikle sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="8f78d-110">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="8f78d-111">Çıkarım parametre ve dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="8f78d-111">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="8f78d-112">Bir parametre listesinde her parametresinin türü belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8f78d-112">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="8f78d-113">Henüz, F # bir statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="8f78d-113">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="8f78d-114">Açıkça belirtmeyin türleri için derleyici bağlamına dayalı türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f78d-114">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="8f78d-115">Belirtilen tür Aksi durumda değilse, genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="8f78d-115">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="8f78d-116">Kod bir değer tutarsız kullanıyorsa, bir şekilde olduğunu Hayır tek bir değer tüm kullanımlarını derleyici bir hata bildirir karşılayan türü sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="8f78d-116">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="8f78d-117">Bir işlevin dönüş türü, işlev son ifade türü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-117">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="8f78d-118">Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü tüm çıkarımı yapılan olmasını `int` çünkü sabit `100` türü `int`.</span><span class="sxs-lookup"><span data-stu-id="8f78d-118">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="8f78d-119">Tür çıkarımı değişmez değerleri değiştirerek etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-119">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="8f78d-120">Yaptığınız `100` bir `uint32` soneki ekleyerek `u`, türlerini `a`, `b`, ve dönüş değeri olarak olayla `uint32`.</span><span class="sxs-lookup"><span data-stu-id="8f78d-120">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="8f78d-121">Ayrıca etkileyebilir çıkarım işlevleri ve yalnızca belirli bir türü ile çalışmayı yöntemleri gibi türü kısıtlamalar kapsıyor diğer yapıları kullanarak yazın.</span><span class="sxs-lookup"><span data-stu-id="8f78d-121">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="8f78d-122">Ayrıca, açık tür ek açıklamaları işlev veya yöntem parametrelerini veya değişkenlerini ifadelerde, aşağıdaki örneklerde gösterildiği gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f78d-122">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="8f78d-123">Farklı kısıtlamaları arasında çakışma meydana gelirse hatalar neden.</span><span class="sxs-lookup"><span data-stu-id="8f78d-123">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="8f78d-124">Bir işlevin dönüş değeri türü ek açıklama tüm parametreleri sağlayarak açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f78d-124">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="8f78d-125">Türü ek açıklama bir parametresini yararlı olduğu ortak bir nesne türü parametresi olduğunda ve bir üye kullanmak istediğiniz durumdur.</span><span class="sxs-lookup"><span data-stu-id="8f78d-125">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="8f78d-126">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="8f78d-126">Automatic Generalization</span></span>
<span data-ttu-id="8f78d-127">İşlev kodu bağımlı bir parametrenin türü üzerinde değilse, genel olarak parametresi derleyici göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="8f78d-127">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="8f78d-128">Bu adlı *otomatik Genelleştirme*, ve karmaşıklık artırmadan genel kod yazma için güçlü bir yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-128">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="8f78d-129">Örneğin, aşağıdaki işlev iki parametre tanımlama grubu içine herhangi bir türde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="8f78d-129">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="8f78d-130">Tür çıkarımı yapılan olmalıdır</span><span class="sxs-lookup"><span data-stu-id="8f78d-130">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="8f78d-131">Ek Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8f78d-131">Additional Information</span></span>
<span data-ttu-id="8f78d-132">Tür çıkarımı F # dil belirtimi bölümlerinde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f78d-132">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="8f78d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f78d-133">See Also</span></span>
[<span data-ttu-id="8f78d-134">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="8f78d-134">Automatic Generalization</span></span>](generics/automatic-generalization.md)
