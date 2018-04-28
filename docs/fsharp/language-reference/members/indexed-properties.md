---
title: Dizini Oluşturulan Özellikler (F#)
description: 'Sıralı verilerine dizi benzeri erişim sağlayan özellikleri olan F # dizin oluşturulmuş özellikleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 39396b3a5ec43f9a8ab0df96afeb69e05801c752
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="indexed-properties"></a><span data-ttu-id="eda80-103">Dizini Oluşturulan Özellikler</span><span class="sxs-lookup"><span data-stu-id="eda80-103">Indexed Properties</span></span>

<span data-ttu-id="eda80-104">*Dizin oluşturulmuş özellikleri* dizi benzeri erişim sağlayan özellikler veri sıralanır.</span><span class="sxs-lookup"><span data-stu-id="eda80-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="eda80-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eda80-105">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="eda80-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eda80-106">Remarks</span></span>
<span data-ttu-id="eda80-107">Üç tür önceki sözdizimi hem de Dizinlenmiş özelliklerin nasıl tanımlanacağı Göster bir `get` ve `set` yöntemi, sahip bir `get` yöntemi yalnızca, veya bir `set` yalnızca yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eda80-107">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="eda80-108">Her ikisi de yalnızca get ve yalnızca kümesi için sözdizimini sözdizimini birleştirebilir ve hem get hem de kümesine sahip bir özellik üretir.</span><span class="sxs-lookup"><span data-stu-id="eda80-108">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="eda80-109">Bu ikinci form farklı erişilebilirlik değiştiricileri ve öznitelikleri almada yerleştirin ve yöntemleri ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda80-109">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="eda80-110">Zaman *PropertyName* olan `Item`, derleyici özelliği bir varsayılan dizin oluşturulmuş özellik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="eda80-110">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="eda80-111">A *varsayılan dizin oluşturulmuş özellik* nesne örneğinde dizi benzeri sözdizimi kullanarak erişebileceğiniz bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="eda80-111">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="eda80-112">Örneğin, varsa `obj` bu özellik, söz dizimi tanımlayan türünde bir nesne `obj.[index]` özelliğine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eda80-112">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="eda80-113">Varsayılan olmayan dizin oluşturulmuş özellik erişmek için söz dizimi özelliğin adını ve parantez içinde dizin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="eda80-113">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="eda80-114">Örneğin, özellik ise `Ordinal`, yazdığınız `obj.Ordinal(index)` erişmek için.</span><span class="sxs-lookup"><span data-stu-id="eda80-114">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="eda80-115">Kullandığınız formdan bağımsız olarak, curried form için her zaman kullanmalısınız `set` dizinlenmiş özelliğine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eda80-115">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="eda80-116">Curried işlevleri hakkında daha fazla bilgi için bkz: [işlevler](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="eda80-116">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="eda80-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="eda80-117">Example</span></span>

<span data-ttu-id="eda80-118">Aşağıdaki kod örneği, tanım ve varsayılan ve get ve set yöntemlerinin varsayılan olmayan Dizinli Özellikler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eda80-118">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="eda80-119">Çıkış</span><span class="sxs-lookup"><span data-stu-id="eda80-119">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="eda80-120">Birden çok dizin değişkenleriyle Dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="eda80-120">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="eda80-121">Dizinli Özellikler birden fazla dizin değişkeni olabilir.</span><span class="sxs-lookup"><span data-stu-id="eda80-121">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="eda80-122">Özelliği kullanıldığında, bu durumda, değişkenleri virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="eda80-122">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="eda80-123">Böyle bir özellik kümesi yönteminde anahtarları içeren bir tanımlama grubu ilki, ikinci ayarlanan değer ise iki curried bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eda80-123">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="eda80-124">Aşağıdaki kod, birden çok dizin değişkenleriyle dizinli bir özelliği kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="eda80-124">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="eda80-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eda80-125">See Also</span></span>
[<span data-ttu-id="eda80-126">Üyeler</span><span class="sxs-lookup"><span data-stu-id="eda80-126">Members</span></span>](index.md)
