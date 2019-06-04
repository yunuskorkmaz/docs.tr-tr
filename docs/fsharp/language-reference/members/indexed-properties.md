---
title: Dizini Oluşturulan Özellikler
description: Dizinli Özellikler hakkında bilgi edinin F#, sıralı verilerine dizi benzeri erişim verin.
ms.date: 10/17/2018
ms.openlocfilehash: 7fc8f46e029255c6ed985a43b92c8f7c2908c428
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489483"
---
# <a name="indexed-properties"></a><span data-ttu-id="091a4-103">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="091a4-103">Indexed Properties</span></span>

<span data-ttu-id="091a4-104">Sıralanmış veriler üzerinde soyutlayan bir sınıf tanımlanırken, bazen temel uygulamayı sokmadan verileri dizinlenmiş erişim sağlamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="091a4-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="091a4-105">Bunun `Item` üyesi.</span><span class="sxs-lookup"><span data-stu-id="091a4-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="091a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="091a4-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="091a4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="091a4-107">Remarks</span></span>

<span data-ttu-id="091a4-108">Her ikisi de Dizinlenmiş özelliklerin nasıl tanımlanacağı önceki sözdizimi formlarda gösterilen bir `get` ve `set` yöntemi sahip bir `get` yöntemi yalnızca veya bir `set` yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="091a4-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="091a4-109">Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirin ve hem get hem de kümesi olan bir özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="091a4-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="091a4-110">Bu ikinci form üzerinde get farklı erişilebilirlik değiştiricileri ve öznitelikleri yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="091a4-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="091a4-111">Adını kullanarak `Item`, derleyici özelliği bir varsayılan dizini oluşturulan özellik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="091a4-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="091a4-112">A *varsayılan dizini oluşturulan özellik* Pro instanci objektu dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="091a4-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="091a4-113">Örneğin, varsa `o` bu özellik, söz dizimi tanımlayan türünde bir nesnedir `o.[index]` özelliğine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="091a4-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="091a4-114">Varsayılan olmayan bir dizinlenmiş özellik erişmek için söz dizimi, özellik ve normal üye olduğu gibi parantez içinde dizin adını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="091a4-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="091a4-115">Örneğin, özellikte `o` çağrılır `Ordinal`, yazdığınız `o.Ordinal(index)` erişmek için.</span><span class="sxs-lookup"><span data-stu-id="091a4-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="091a4-116">Kullandığınız formdan bakılmaksızın, bir dizinlenmiş özellik kümesi yöntemi için curried formu her zaman kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="091a4-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="091a4-117">Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="091a4-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="091a4-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="091a4-118">Example</span></span>

<span data-ttu-id="091a4-119">Aşağıdaki kod örneği, varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="091a4-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="091a4-120">Çıkış</span><span class="sxs-lookup"><span data-stu-id="091a4-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="091a4-121">Birden çok dizin değerlerle dizini oluşturulan özellikler</span><span class="sxs-lookup"><span data-stu-id="091a4-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="091a4-122">Dizinli Özellikler birden fazla dizin değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="091a4-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="091a4-123">Özelliği kullanıldığında, bu durumda, değerler virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="091a4-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="091a4-124">Böyle bir özellik kümesi yöntemi bilgisayarının ilki anahtarları içeren bir tanımlama grubu ve ikinci değer ayarlamak için iki curried bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="091a4-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="091a4-125">Aşağıdaki kod, birden çok dizin değerlerini içeren bir dizini oluşturulmuş özelliğe kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="091a4-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="091a4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="091a4-126">See also</span></span>

- [<span data-ttu-id="091a4-127">Üyeler</span><span class="sxs-lookup"><span data-stu-id="091a4-127">Members</span></span>](index.md)
