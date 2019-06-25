---
title: ReadOnly anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348019"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="f45cd-102">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f45cd-102">readonly (C# Reference)</span></span>

<span data-ttu-id="f45cd-103">`readonly` Anahtar sözcüğü, üç bağlamlarda kullanılan bir değiştirici:</span><span class="sxs-lookup"><span data-stu-id="f45cd-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="f45cd-104">İçinde bir [alan bildirimi](#readonly-field-example), `readonly` alana atama bildirimin veya aynı sınıftaki bir oluşturucunun parçası olarak yalnızca oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="f45cd-105">Salt okunur bir alan atanabilir ve alan bildirimi ve oluşturucu içinde birden çok kez yeniden atandı.</span><span class="sxs-lookup"><span data-stu-id="f45cd-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="f45cd-106">A `readonly` alan oluşturucu çıktıktan sonra atanamaz.</span><span class="sxs-lookup"><span data-stu-id="f45cd-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="f45cd-107">Değer türleri ve başvuru türleri için farklı biçimlerde olan:</span><span class="sxs-lookup"><span data-stu-id="f45cd-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="f45cd-108">Değer türleri verilerini doğrudan içerdiği için olan bir alan bir `readonly` değişmez değer türü.</span><span class="sxs-lookup"><span data-stu-id="f45cd-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="f45cd-109">Başvuru türleri verilerine bir başvuru içerdiğinden olan bir alan bir `readonly` başvuru türü her zaman aynı nesneye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f45cd-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="f45cd-110">Bu nesne sabit değil.</span><span class="sxs-lookup"><span data-stu-id="f45cd-110">That object is not immutable.</span></span> <span data-ttu-id="f45cd-111">`readonly` Değiştiricisi başvuru türü farklı bir örneğine yerini alan engeller.</span><span class="sxs-lookup"><span data-stu-id="f45cd-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="f45cd-112">Ancak değiştiricisi, örnek veri alanının salt okunur alanı değiştirilmiş engellemez.</span><span class="sxs-lookup"><span data-stu-id="f45cd-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="f45cd-113">Dışarıdan görünen tür, kesilebilir başvuru türü olan bir dışarıdan görünen salt okunur alan içeren bir güvenlik açığı olabilir ve uyarı tetikleyebilir [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Salt okunur kesilebilir başvuru türleri bildirmeyin."</span><span class="sxs-lookup"><span data-stu-id="f45cd-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="f45cd-114">İçinde bir [ `readonly struct` tanımı](#readonly-struct-example), `readonly` belirten `struct` sabittir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="f45cd-115">İçinde bir [ `ref readonly` yöntemi dönüş](#ref-readonly-return-example), `readonly` değiştiricisi gösteren bir başvuru ve yazma işlemleri bu başvurusuna izin verilmez yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f45cd-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="f45cd-116">Son iki bağlamdan, C# 7.2 eklendi.</span><span class="sxs-lookup"><span data-stu-id="f45cd-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="f45cd-117">Salt okunur alanı örneği</span><span class="sxs-lookup"><span data-stu-id="f45cd-117">Readonly field example</span></span>

<span data-ttu-id="f45cd-118">Bu örnekte, alanın değerini `year` yöntemi değiştirilemez `ChangeYear`rağmen sınıf oluşturucusu bir değer atanır:</span><span class="sxs-lookup"><span data-stu-id="f45cd-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="f45cd-119">Bir değer atamak için bir `readonly` yalnızca şu bağlamlarda alan:</span><span class="sxs-lookup"><span data-stu-id="f45cd-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="f45cd-120">Ne zaman Değişken bildiriminde örneğin başlatılır:</span><span class="sxs-lookup"><span data-stu-id="f45cd-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="f45cd-121">Bir sınıfın örnek oluşturucusunda örnek alan bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="f45cd-122">Statik Oluşturucu sınıfın statik alan bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="f45cd-123">Bu oluşturucu bağlamları de yalnızca bağlamları olduğu geçirmek için geçerli olan bir `readonly` olarak alan bir [kullanıma](out-parameter-modifier.md) veya [ref](ref.md) parametresi.</span><span class="sxs-lookup"><span data-stu-id="f45cd-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="f45cd-124">`readonly` Anahtar sözcüğü, farklı [const](const.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f45cd-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="f45cd-125">A `const` alanı alanın bildiriminde yalnızca başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="f45cd-126">A `readonly` alan alan bildirimi ve herhangi bir oluşturucu birden çok kez atanabilir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="f45cd-127">Bu nedenle, `readonly` alanları kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="f45cd-128">Ayrıca, while bir `const` alandır bir derleme zamanı sabiti `readonly` alan, aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f45cd-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="f45cd-129">Önceki örnekte, aşağıdaki örnekte olduğu gibi bir deyim kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="f45cd-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="f45cd-130">Derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="f45cd-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="f45cd-131">Salt okunur yapı örneği</span><span class="sxs-lookup"><span data-stu-id="f45cd-131">Readonly struct example</span></span>

<span data-ttu-id="f45cd-132">`readonly` Değiştiricisi bir `struct` tanımı, yapı olduğunu bildirir **değişmez**.</span><span class="sxs-lookup"><span data-stu-id="f45cd-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="f45cd-133">Her örnek alan `struct` işaretlenmelidir `readonly`, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="f45cd-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="f45cd-134">Önceki örnekte [salt okunur otomatik özellikleri](../../properties.md#read-only) depolamasını bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="f45cd-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="f45cd-135">Derleyicinin oluşturmasını söyler `readonly` destek alanları için bu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f45cd-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="f45cd-136">Ayrıca bildirip `readonly` doğrudan alanlar:</span><span class="sxs-lookup"><span data-stu-id="f45cd-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="f45cd-137">İşaretlenmemiş bir alan ekleme `readonly` derleyici hatası oluşturur `CS8340`: "Salt okunur yapı birimlerinin örnek alanları salt okunur olmalıdır."</span><span class="sxs-lookup"><span data-stu-id="f45cd-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="f45cd-138">Ref salt okunur dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="f45cd-138">Ref readonly return example</span></span>

<span data-ttu-id="f45cd-139">`readonly` Değiştiricisi bir `ref return` döndürülen başvuru değiştirilemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f45cd-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="f45cd-140">Aşağıdaki örnek, kaynağı bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="f45cd-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="f45cd-141">Kullandığı `readonly` değiştiricisi arayanları kaynağı değiştirilemiyor belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="f45cd-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="f45cd-142">Döndürülen tür olması gerekmez bir `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="f45cd-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="f45cd-143">Tarafından döndürülen herhangi bir türü `ref` tarafından döndürülen `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="f45cd-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f45cd-144">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f45cd-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f45cd-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f45cd-145">See also</span></span>

- [<span data-ttu-id="f45cd-146">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f45cd-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f45cd-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f45cd-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f45cd-148">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f45cd-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f45cd-149">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="f45cd-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="f45cd-150">const</span><span class="sxs-lookup"><span data-stu-id="f45cd-150">const</span></span>](const.md)
- [<span data-ttu-id="f45cd-151">Alanlar</span><span class="sxs-lookup"><span data-stu-id="f45cd-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
