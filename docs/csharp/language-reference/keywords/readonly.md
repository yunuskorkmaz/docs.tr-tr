---
title: ReadOnly anahtar sözcüğü (C# Başvurusu)
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d09ce4ea972a3064298eebdf0b8b80999ee8441e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227291"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="1d970-102">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1d970-102">readonly (C# Reference)</span></span>

<span data-ttu-id="1d970-103">`readonly` Anahtar sözcüğü, üç bağlamlarda kullanılan bir değiştirici:</span><span class="sxs-lookup"><span data-stu-id="1d970-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="1d970-104">İçinde bir [alan bildirimi](#readonly-field-example), `readonly` alana atama bildirimin veya aynı sınıftaki bir oluşturucunun parçası olarak yalnızca oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d970-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span>
- <span data-ttu-id="1d970-105">İçinde bir [ `readonly struct` tanımı](#readonly-struct-example), `readonly` belirten `struct` sabittir.</span><span class="sxs-lookup"><span data-stu-id="1d970-105">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="1d970-106">İçinde bir [ `ref readonly` yöntemi dönüş](#ref-readonly-return-example), `readonly` değiştiricisi gösteren bir başvuru ve yazma işlemleri bu başvurusuna izin verilmez yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d970-106">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="1d970-107">Son iki bağlamdan, C# 7.2 eklendi.</span><span class="sxs-lookup"><span data-stu-id="1d970-107">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="1d970-108">Salt okunur alanı örneği</span><span class="sxs-lookup"><span data-stu-id="1d970-108">Readonly field example</span></span>

<span data-ttu-id="1d970-109">Bu örnekte, alanın değerini `year` yöntemi değiştirilemez `ChangeYear`rağmen sınıf oluşturucusu bir değer atanır:</span><span class="sxs-lookup"><span data-stu-id="1d970-109">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="1d970-110">Bir değer atamak için bir `readonly` yalnızca şu bağlamlarda alan:</span><span class="sxs-lookup"><span data-stu-id="1d970-110">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="1d970-111">Ne zaman Değişken bildiriminde örneğin başlatılır:</span><span class="sxs-lookup"><span data-stu-id="1d970-111">When the variable is initialized in the declaration, for example:</span></span>

```csharp
public readonly int y = 5;
```

- <span data-ttu-id="1d970-112">Bir sınıfın örnek oluşturucusunda örnek alan bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="1d970-112">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="1d970-113">Statik Oluşturucu sınıfın statik alan bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="1d970-113">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="1d970-114">Bu oluşturucu bağlamları de yalnızca bağlamları olduğu geçirmek için geçerli olan bir `readonly` olarak alan bir [kullanıma](out-parameter-modifier.md) veya [ref](ref.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="1d970-114">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="1d970-115">`readonly` Anahtar sözcüğü, farklı [const](const.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1d970-115">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="1d970-116">A `const` alanı alanın bildiriminde yalnızca başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d970-116">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="1d970-117">A `readonly` alanı bildirimde veya oluşturucuda başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d970-117">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="1d970-118">Bu nedenle, `readonly` alanları kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d970-118">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="1d970-119">Ayrıca, while bir `const` alandır bir derleme zamanı sabiti `readonly` alan, aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d970-119">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="1d970-120">Önceki örnekte, aşağıdaki örnekte olduğu gibi bir deyim kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="1d970-120">In the preceding example, if you use a statement like the following example:</span></span>

`p2.y = 66;        // Error`

<span data-ttu-id="1d970-121">Derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1d970-121">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="1d970-122">Salt okunur yapı örneği</span><span class="sxs-lookup"><span data-stu-id="1d970-122">Readonly struct example</span></span>

<span data-ttu-id="1d970-123">`readonly` Değiştiricisi bir `struct` tanımı, yapı olduğunu bildirir **değişmez**.</span><span class="sxs-lookup"><span data-stu-id="1d970-123">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="1d970-124">Her örnek alan `struct` işaretlenmelidir `readonly`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="1d970-124">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="1d970-125">Önceki örnekte [salt okunur otomatik özellikleri](../../properties.md#read-only) depolamasını bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="1d970-125">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="1d970-126">Derleyicinin oluşturmasını söyler `readonly` destek alanları için bu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1d970-126">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="1d970-127">Ayrıca bildirip `readonly` doğrudan alanlar:</span><span class="sxs-lookup"><span data-stu-id="1d970-127">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="1d970-128">İşaretlenmemiş bir alan ekleme `readonly` derleyici hatası oluşturur `CS8340`: "salt okunur yapı birimlerinin örnek alanları salt okunur olmalıdır."</span><span class="sxs-lookup"><span data-stu-id="1d970-128">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="1d970-129">Ref salt okunur dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="1d970-129">Ref readonly return example</span></span>

<span data-ttu-id="1d970-130">`readonly` Değiştiricisi bir `ref return` döndürülen başvuru değiştirilemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d970-130">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="1d970-131">Aşağıdaki örnek, kaynağı bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="1d970-131">The following example returns a reference to the origin.</span></span> <span data-ttu-id="1d970-132">Kullandığı `readonly` değiştiricisi arayanları kaynağı değiştirilemiyor belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="1d970-132">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="1d970-133">Döndürülen tür olması gerekmez bir `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="1d970-133">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="1d970-134">Tarafından döndürülen herhangi bir türü `ref` tarafından döndürülen `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="1d970-134">Any type that can be returned by `ref` can be returned by `ref readonly`</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d970-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d970-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1d970-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d970-136">See also</span></span>

- [<span data-ttu-id="1d970-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d970-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d970-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1d970-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d970-139">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1d970-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d970-140">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="1d970-140">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="1d970-141">const</span><span class="sxs-lookup"><span data-stu-id="1d970-141">const</span></span>](const.md)
- [<span data-ttu-id="1d970-142">Alanlar</span><span class="sxs-lookup"><span data-stu-id="1d970-142">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
