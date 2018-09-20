---
title: Dizini Oluşturulan Özellikler (F#)
description: 'Sıralı verilerine dizi benzeri erişim sağlayan özellikleri olan F # dizinli özellikleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46321372"
---
# <a name="indexed-properties"></a><span data-ttu-id="e5e07-103">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5e07-103">Indexed Properties</span></span>

<span data-ttu-id="e5e07-104">*Dizin oluşturulmuş özellikleri* dizi benzeri erişim sağlayan özellikler veri sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e5e07-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="e5e07-105">Üç formlarında geldikleri:</span><span class="sxs-lookup"><span data-stu-id="e5e07-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="e5e07-106">Bir F # üye bir dizi benzeri erişim sağlamak için bu üç ad adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5e07-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="e5e07-107">`IndexerName` Aşağıdaki üç seçenekten birini temsil etmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e5e07-107">`IndexerName` is used to represent any of the three options below:</span></span>

## <a name="syntax"></a><span data-ttu-id="e5e07-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5e07-108">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="e5e07-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5e07-109">Remarks</span></span>

<span data-ttu-id="e5e07-110">Her ikisi de Dizinlenmiş özelliklerin nasıl tanımlanacağı önceki sözdizimi formlarda gösterilen bir `get` ve `set` yöntemi sahip bir `get` yöntemi yalnızca veya bir `set` yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5e07-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="e5e07-111">Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirin ve hem get hem de kümesi olan bir özellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5e07-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="e5e07-112">Bu ikinci form üzerinde get farklı erişilebilirlik değiştiricileri ve öznitelikleri yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5e07-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="e5e07-113">Zaman *IndexerName* olduğu `Item`, derleyici özelliği bir varsayılan dizini oluşturulan özellik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="e5e07-114">A *varsayılan dizini oluşturulan özellik* Pro instanci objektu dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="e5e07-115">Örneğin, varsa `obj` bu özellik, söz dizimi tanımlayan türünde bir nesnedir `obj.[index]` özelliğine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5e07-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="e5e07-116">Varsayılan olmayan dizine özelliğine erişmek için söz dizimi, özelliğin adını ve parantez içinde dizin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e5e07-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="e5e07-117">Örneğin, özellik ise `Ordinal`, yazdığınız `obj.Ordinal(index)` erişmek için.</span><span class="sxs-lookup"><span data-stu-id="e5e07-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="e5e07-118">Kullandığınız formdan ne olursa olsun, curried form için her zaman kullanmalısınız `set` bir dizinlenmiş özellik yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5e07-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="e5e07-119">Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevleri](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5e07-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5e07-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5e07-120">Example</span></span>

<span data-ttu-id="e5e07-121">Aşağıdaki kod örneği, varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="e5e07-122">Çıkış</span><span class="sxs-lookup"><span data-stu-id="e5e07-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="e5e07-123">Birden çok dizin değişkenleriyle dizini oluşturulan özellikler</span><span class="sxs-lookup"><span data-stu-id="e5e07-123">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="e5e07-124">Dizinli Özellikler birden fazla dizin değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="e5e07-125">Özelliği kullanıldığında, bu durumda, değişkenlerin virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e5e07-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="e5e07-126">Böyle bir özellik kümesi yöntemi ilki anahtarları içeren bir tanımlama grubu, ve ikinci ayarlanan değer iki curried bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="e5e07-127">Aşağıdaki kod, birden çok dizin değişkenleri içeren bir dizini oluşturulmuş özelliğe kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5e07-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="e5e07-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5e07-128">See also</span></span>

- [<span data-ttu-id="e5e07-129">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e5e07-129">Members</span></span>](index.md)
