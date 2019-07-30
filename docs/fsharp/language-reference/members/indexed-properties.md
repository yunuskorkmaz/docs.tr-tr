---
title: Dizini Oluşturulan Özellikler
description: İçindeki F#dizinli özellikler hakkında bilgi edinin. Bu, sıralı verilere dizi benzeri erişim sağlar.
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627562"
---
# <a name="indexed-properties"></a><span data-ttu-id="3250f-103">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="3250f-103">Indexed Properties</span></span>

<span data-ttu-id="3250f-104">Sıralı verileri soyutlayan bir sınıf tanımlarken, bu verilere, temel alınan uygulamayı kullanıma açmadan dizin oluşturma erişimi sağlamak bazen yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3250f-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="3250f-105">Bu, `Item` üyeyle yapılır.</span><span class="sxs-lookup"><span data-stu-id="3250f-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="3250f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3250f-106">Syntax</span></span>

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="3250f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3250f-107">Remarks</span></span>

<span data-ttu-id="3250f-108">Önceki sözdiziminin `get` formları, hem a `set` hem de yöntemine sahip dizinlenmiş özelliklerin nasıl tanımlanacağını, yalnızca bir `get` yöntemine sahip olduğunu veya yalnızca bir `set` yöntemine sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3250f-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="3250f-109">Ayrıca, yalnızca Get için gösterilen sözdizimini ve yalnızca set için gösterilen sözdizimini birleştirebilir ve hem Get hem de set içeren bir özellik oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3250f-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="3250f-110">Bu ikinci form, Get ve set yöntemlerine farklı erişilebilirlik değiştiricileri ve öznitelikler eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3250f-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="3250f-111">Ad `Item`kullanıldığında, derleyici özelliği varsayılan dizinli bir özellik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="3250f-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="3250f-112">*Varsayılan dizinli* bir özellik, nesne örneğinde dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="3250f-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="3250f-113">Örneğin, bu özelliği `o` tanımlayan türün bir nesneslarsa, özelliğine erişmek için sözdizimi `o.[index]` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3250f-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="3250f-114">Varsayılan olmayan bir dizinli özelliğe erişim sözdizimi, bir normal üye gibi, özelliğin adını ve parantez içinde dizin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3250f-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="3250f-115">Örneğin, üzerindeki `o` özelliği çağrılırsa `Ordinal`, ona erişmek için yazarsınız `o.Ordinal(index)` .</span><span class="sxs-lookup"><span data-stu-id="3250f-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="3250f-116">Kullandığınız formdan bağımsız olarak, dizinlenmiş bir özellikte set yöntemi için her zaman curried formunu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3250f-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="3250f-117">Curried işlevleri hakkında bilgi için bkz. [işlevler](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3250f-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="3250f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3250f-118">Example</span></span>

<span data-ttu-id="3250f-119">Aşağıdaki kod örneği, Get ve set yöntemlerine sahip varsayılan ve varsayılan olmayan dizinli özelliklerin tanımını ve kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3250f-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="3250f-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="3250f-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="3250f-121">Birden çok dizin değeri olan dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="3250f-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="3250f-122">Dizinli Özellikler birden fazla dizin değerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3250f-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="3250f-123">Bu durumda, özellik kullanıldığında değerler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="3250f-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="3250f-124">Böyle bir özelliğindeki set yöntemi iki curried bağımsız değişkene sahip olmalıdır, ilki anahtarları içeren bir tanımlama grubu ve ikincisinin ayarlandığı değer.</span><span class="sxs-lookup"><span data-stu-id="3250f-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="3250f-125">Aşağıdaki kod, birden çok dizin değeri olan dizinli bir özelliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3250f-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="3250f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3250f-126">See also</span></span>

- [<span data-ttu-id="3250f-127">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3250f-127">Members</span></span>](index.md)
