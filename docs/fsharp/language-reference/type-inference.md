---
title: Tür Çıkarma (F#)
description: 'F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563712"
---
# <a name="type-inference"></a><span data-ttu-id="4d01c-103">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="4d01c-103">Type Inference</span></span>

<span data-ttu-id="4d01c-104">Bu konu, F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d01c-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="4d01c-105">Genel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="4d01c-105">Type Inference in General</span></span>
<span data-ttu-id="4d01c-106">Tür çıkarımı fikri zaman derleyici conclusively türünü türetme edilemez dışında F # yapılarını türlerini belirtmek gerekmez değildir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="4d01c-107">Açık tür bilgileri atlama F # dinamik olarak yazılan bir dil olan veya değerleri F # zayıf yazılmış anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="4d01c-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="4d01c-108">F # derleyici derleme sırasında her bir yapı için tam bir türe deduces anlamına gelen bir statik olarak belirtilmiş, dilidir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="4d01c-109">Her yapı türleri türetme derleyici için yeterli bilgi değilse açık tür ek açıklama herhangi bir yerde kodda ekleyerek ek tür bilgileri, genellikle sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="4d01c-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="4d01c-110">Çıkarım parametre ve dönüş türleri</span><span class="sxs-lookup"><span data-stu-id="4d01c-110">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="4d01c-111">Bir parametre listesinde her parametresinin türü belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4d01c-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="4d01c-112">Henüz, F # bir statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifade derleme zamanında kesin bir türe sahip.</span><span class="sxs-lookup"><span data-stu-id="4d01c-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="4d01c-113">Açıkça belirtmeyin türleri için derleyici bağlamına dayalı türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4d01c-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="4d01c-114">Belirtilen tür Aksi durumda değilse, genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="4d01c-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="4d01c-115">Kod bir değer tutarsız kullanıyorsa, bir şekilde olduğunu Hayır tek bir değer tüm kullanımlarını derleyici bir hata bildirir karşılayan türü sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="4d01c-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="4d01c-116">Bir işlevin dönüş türü, işlev son ifade türü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="4d01c-117">Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü tüm çıkarımı yapılan olmasını `int` çünkü sabit `100` türü `int`.</span><span class="sxs-lookup"><span data-stu-id="4d01c-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="4d01c-118">Tür çıkarımı değişmez değerleri değiştirerek etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="4d01c-119">Yaptığınız `100` bir `uint32` soneki ekleyerek `u`, türlerini `a`, `b`, ve dönüş değeri olarak olayla `uint32`.</span><span class="sxs-lookup"><span data-stu-id="4d01c-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="4d01c-120">Ayrıca etkileyebilir çıkarım işlevleri ve yalnızca belirli bir türü ile çalışmayı yöntemleri gibi türü kısıtlamalar kapsıyor diğer yapıları kullanarak yazın.</span><span class="sxs-lookup"><span data-stu-id="4d01c-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="4d01c-121">Ayrıca, açık tür ek açıklamaları işlev veya yöntem parametrelerini veya değişkenlerini ifadelerde, aşağıdaki örneklerde gösterildiği gibi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d01c-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="4d01c-122">Farklı kısıtlamaları arasında çakışma meydana gelirse hatalar neden.</span><span class="sxs-lookup"><span data-stu-id="4d01c-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="4d01c-123">Bir işlevin dönüş değeri türü ek açıklama tüm parametreleri sağlayarak açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d01c-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="4d01c-124">Türü ek açıklama bir parametresini yararlı olduğu ortak bir nesne türü parametresi olduğunda ve bir üye kullanmak istediğiniz durumdur.</span><span class="sxs-lookup"><span data-stu-id="4d01c-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="4d01c-125">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d01c-125">Automatic Generalization</span></span>
<span data-ttu-id="4d01c-126">İşlev kodu bağımlı bir parametrenin türü üzerinde değilse, genel olarak parametresi derleyici göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="4d01c-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="4d01c-127">Bu adlı *otomatik Genelleştirme*, ve karmaşıklık artırmadan genel kod yazma için güçlü bir yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="4d01c-128">Örneğin, aşağıdaki işlev iki parametre tanımlama grubu içine herhangi bir türde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4d01c-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="4d01c-129">Tür çıkarımı yapılan olmalıdır</span><span class="sxs-lookup"><span data-stu-id="4d01c-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="4d01c-130">Ek Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4d01c-130">Additional Information</span></span>
<span data-ttu-id="4d01c-131">Tür çıkarımı F # dil belirtimi bölümlerinde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d01c-131">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="4d01c-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d01c-132">See Also</span></span>
[<span data-ttu-id="4d01c-133">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d01c-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
