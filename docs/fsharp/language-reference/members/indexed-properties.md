---
title: Dizini Oluşturulan Özellikler (F#)
description: Dizinli Özellikler hakkında bilgi edinin F#, sıralı verilerine dizi benzeri erişim verin.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "49452254"
---
# <a name="indexed-properties"></a><span data-ttu-id="daa83-103">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="daa83-103">Indexed Properties</span></span>

<span data-ttu-id="daa83-104">Sıralanmış veriler üzerinde soyutlayan bir sınıf tanımlanırken, bazen temel uygulamayı sokmadan verileri dizinlenmiş erişim sağlamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="daa83-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="daa83-105">Bunun `Index` üyesi.</span><span class="sxs-lookup"><span data-stu-id="daa83-105">This is done with the `Index` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="daa83-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daa83-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="daa83-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daa83-107">Remarks</span></span>

<span data-ttu-id="daa83-108">Her ikisi de Dizinlenmiş özelliklerin nasıl tanımlanacağı önceki sözdizimi formlarda gösterilen bir `get` ve `set` yöntemi sahip bir `get` yöntemi yalnızca veya bir `set` yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="daa83-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="daa83-109">Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirin ve hem get hem de kümesi olan bir özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="daa83-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="daa83-110">Bu ikinci form üzerinde get farklı erişilebilirlik değiştiricileri ve öznitelikleri yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="daa83-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="daa83-111">Adını kullanarak `Item`, derleyici özelliği bir varsayılan dizini oluşturulan özellik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="daa83-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="daa83-112">A *varsayılan dizini oluşturulan özellik* Pro instanci objektu dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="daa83-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="daa83-113">Örneğin, varsa `o` bu özellik, söz dizimi tanımlayan türünde bir nesnedir `o.[index]` özelliğine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="daa83-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="daa83-114">Varsayılan olmayan bir dizinlenmiş özellik erişmek için söz dizimi, özellik ve normal üye olduğu gibi parantez içinde dizin adını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="daa83-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="daa83-115">Örneğin, özellikte `o` çağrılır `Ordinal`, yazdığınız `o.Ordinal(index)` erişmek için.</span><span class="sxs-lookup"><span data-stu-id="daa83-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="daa83-116">Kullandığınız formdan bakılmaksızın, bir dizinlenmiş özellik kümesi yöntemi için curried formu her zaman kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="daa83-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="daa83-117">Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="daa83-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="daa83-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="daa83-118">Example</span></span>

<span data-ttu-id="daa83-119">Aşağıdaki kod örneği, varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="daa83-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="daa83-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="daa83-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="daa83-121">Birden çok dizin değişkenleriyle dizini oluşturulan özellikler</span><span class="sxs-lookup"><span data-stu-id="daa83-121">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="daa83-122">Dizinli Özellikler birden fazla dizin değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="daa83-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="daa83-123">Özelliği kullanıldığında, bu durumda, değişkenlerin virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="daa83-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="daa83-124">Böyle bir özellik kümesi yöntemi ilki anahtarları içeren bir tanımlama grubu, ve ikinci ayarlanan değer iki curried bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="daa83-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="daa83-125">Aşağıdaki kod, birden çok dizin değişkenleri içeren bir dizini oluşturulmuş özelliğe kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="daa83-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="daa83-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="daa83-126">See also</span></span>

- [<span data-ttu-id="daa83-127">Üyeler</span><span class="sxs-lookup"><span data-stu-id="daa83-127">Members</span></span>](index.md)
