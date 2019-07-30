---
title: Tür Çıkarma
description: F# Derleyicinin değer, değişken, parametre ve dönüş değeri türlerini nasıl kullandığını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630186"
---
# <a name="type-inference"></a><span data-ttu-id="13883-103">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="13883-103">Type Inference</span></span>

<span data-ttu-id="13883-104">Bu konu, F# derleyicinin değer, değişken, parametre ve dönüş değeri türlerini nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="13883-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="13883-105">Genel olarak tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="13883-105">Type Inference in General</span></span>

<span data-ttu-id="13883-106">Tür çıkarımı, derleyicinin türü yaratacağı ne zaman bir F# değer çıkarmadığını hariç, yapı türlerini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="13883-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="13883-107">Açık tür bilgilerinin atlanması, dinamik olarak yazılmış F# bir dil olan veya ' deki F# değerlerin zayıf olarak yazıldığı anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="13883-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="13883-108">F#statik olarak yazılmış bir dildir, bu, derleyicinin derleme sırasında her bir yapı için tam bir tür olarak kesintiler anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="13883-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="13883-109">Derleyicinin her bir yapının türünü vermesini sağlamak için yeterli bilgi yoksa, genellikle kodda bir yere açık tür ek açıklamaları ekleyerek ek tür bilgileri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13883-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="13883-110">Parametre ve dönüş türlerinin çıkarımı</span><span class="sxs-lookup"><span data-stu-id="13883-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="13883-111">Bir parametre listesinde, her parametrenin türünü belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="13883-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="13883-112">Ancak, F# statik olarak yazılmış bir dildir ve bu nedenle her değer ve ifadede derleme zamanında kesin bir tür vardır.</span><span class="sxs-lookup"><span data-stu-id="13883-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="13883-113">Açıkça belirtmedikleri türler için, derleyici bu türü bağlama göre alır.</span><span class="sxs-lookup"><span data-stu-id="13883-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="13883-114">Tür başka bir şekilde belirtilmemişse, genel olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="13883-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="13883-115">Kod, bir değeri tutarsız bir şekilde kullanıyorsa, bir değerin tüm kullanımlarını karşılayan tek bir Çıkarsanan tür yoksa, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="13883-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="13883-116">İşlevin dönüş türü, işlevdeki son ifadenin türüne göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="13883-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="13883-117">Örneğin, aşağıdaki kodda, parametre türleri `a` ve `b` ve dönüş türü, değişmez değer `100` türünde `int`olduğu için `int` hepsi olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="13883-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="13883-118">Sabit değerleri değiştirerek tür çıkarımı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="13883-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="13883-119">`100` `uint32` `uint32` `b`Son Eki`u`ekleyerek bir yaparsanız,,, ve dönüş değerinin türü olarakalgılanır.`a`</span><span class="sxs-lookup"><span data-stu-id="13883-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="13883-120">Tür çıkarımı, yalnızca belirli bir türle çalışan işlevler ve yöntemler gibi tür kısıtlamalarını belirten diğer yapıları kullanarak da etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="13883-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="13883-121">Ayrıca, aşağıdaki örneklerde gösterildiği gibi, işlev veya yöntem parametrelerine ya da deyimlerdeki değişkenlere açık tür ek açıklamaları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13883-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="13883-122">Hatalar, farklı kısıtlamalar arasında çakışmalar oluşursa oluşur.</span><span class="sxs-lookup"><span data-stu-id="13883-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="13883-123">Ayrıca, tüm parametrelerden sonra bir tür ek açıklaması sağlayarak bir işlevin dönüş değerini açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13883-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="13883-124">Bir parametre üzerinde yararlı bir tür ek açıklamanın, parametrenin nesne türü olması ve bir üyeyi kullanmak istediğinizde olduğu yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="13883-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="13883-125">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="13883-125">Automatic Generalization</span></span>

<span data-ttu-id="13883-126">İşlev kodu bir parametre türüne bağımlı değilse, derleyici parametreyi genel olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="13883-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="13883-127">Buna *Otomatik Genelleştirme*denir ve karmaşıklık arttırmadan genel kod yazmak için güçlü bir yardım olabilir.</span><span class="sxs-lookup"><span data-stu-id="13883-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="13883-128">Örneğin, aşağıdaki işlev herhangi bir türdeki iki parametreyi bir tanımlama grubu içinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="13883-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="13883-129">Tür şu şekilde algılanır</span><span class="sxs-lookup"><span data-stu-id="13883-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="13883-130">Ek Bilgiler</span><span class="sxs-lookup"><span data-stu-id="13883-130">Additional Information</span></span>

<span data-ttu-id="13883-131">Tür çıkarımı, F# dil belirtiminde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="13883-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="13883-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13883-132">See also</span></span>

- [<span data-ttu-id="13883-133">Otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="13883-133">Automatic Generalization</span></span>](./generics/automatic-generalization.md)
