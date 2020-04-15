---
title: readonly anahtar kelime - C# Başvuru
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389053"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="93d36-102">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="93d36-102">readonly (C# Reference)</span></span>

<span data-ttu-id="93d36-103">Anahtar `readonly` kelime, dört bağlamda kullanılabilen bir değiştiricidir:</span><span class="sxs-lookup"><span data-stu-id="93d36-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="93d36-104">Alan [bildiriminde,](#readonly-field-example) `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="93d36-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="93d36-105">Yalnızca okunan bir alan, alan bildirimi ve oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="93d36-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="93d36-106">Bir `readonly` alan, yapıcı çıktıktan sonra atanamaz.</span><span class="sxs-lookup"><span data-stu-id="93d36-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="93d36-107">Bu kuralın değer türleri ve başvuru türleri için farklı etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="93d36-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="93d36-108">Değer türleri doğrudan verilerini içerdiğinden, değer `readonly` türü olan bir alan değişmez.</span><span class="sxs-lookup"><span data-stu-id="93d36-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="93d36-109">Başvuru türleri verilerine bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alanın her zaman aynı nesneye başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="93d36-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="93d36-110">Bu nesne değişmez değil.</span><span class="sxs-lookup"><span data-stu-id="93d36-110">That object isn't immutable.</span></span> <span data-ttu-id="93d36-111">Değiştirici, `readonly` alanın başvuru türünün farklı bir örneğiyle değiştirilmesini önler.</span><span class="sxs-lookup"><span data-stu-id="93d36-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="93d36-112">Ancak, değiştirici, alanın örnek verilerinin salt okunur alanı boyunca değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="93d36-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="93d36-113">Mutable başvuru türü olan harici olarak görünür salt okunur alan içeren harici olarak görünen bir tür bir güvenlik açığı olabilir ve [ca2104](/visualstudio/code-quality/ca2104) uyarısını tetikleyebilir: "Yalnızca mutable başvuru türlerini okumayı bildirin."</span><span class="sxs-lookup"><span data-stu-id="93d36-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="93d36-114">Bir `readonly struct` tür tanımında, `readonly` yapı türünün değişmez olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="93d36-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="93d36-115">Daha fazla bilgi [ `readonly` ](../builtin-types/struct.md#readonly-struct) için Yapı [türleri](../builtin-types/struct.md) makalesinin yapı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="93d36-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="93d36-116">Bir yapı türü içindeki bir `readonly` örnek üye bildiriminde, bir örnek üyenin yapının durumunu değiştirmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="93d36-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="93d36-117">Daha fazla bilgi için [Yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` örnek üyeler](../builtin-types/struct.md#readonly-instance-members) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="93d36-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="93d36-118">Yöntem [ `ref readonly` dönüşünde,](#ref-readonly-return-example) `readonly` değiştirici yöntemin bir başvurudöndürür ve bu başvuru için yazı izin verilmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="93d36-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="93d36-119">Ve `readonly struct` `ref readonly` bağlamlar C# 7.2'ye eklendi.</span><span class="sxs-lookup"><span data-stu-id="93d36-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="93d36-120">`readonly`yapı üyeleri C# 8.0'a eklendi</span><span class="sxs-lookup"><span data-stu-id="93d36-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="93d36-121">Readonly alan örneği</span><span class="sxs-lookup"><span data-stu-id="93d36-121">Readonly field example</span></span>

<span data-ttu-id="93d36-122">Bu örnekte, sınıf oluşturucuya bir değer atanmış `ChangeYear`olsa bile, yöntemde alanın `year` değeri değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="93d36-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="93d36-123">Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93d36-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="93d36-124">Değişken bildirimde başharfe geçtiğinde, örneğin:</span><span class="sxs-lookup"><span data-stu-id="93d36-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="93d36-125">Örnek alan bildirimini içeren sınıfın bir örnek oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="93d36-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="93d36-126">Statik alan bildirimini içeren sınıfın statik oluşturucuda.</span><span class="sxs-lookup"><span data-stu-id="93d36-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="93d36-127">Bu oluşturucu bağlamlar, bir `readonly` alanı dış [veya](out-parameter-modifier.md) [ref](ref.md) parametresi olarak geçirmenin geçerli olduğu tek bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="93d36-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="93d36-128">Anahtar `readonly` kelime [const](const.md) anahtar kelime farklıdır.</span><span class="sxs-lookup"><span data-stu-id="93d36-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="93d36-129">Bir `const` alan yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="93d36-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="93d36-130">Alan `readonly` bildiriminde ve herhangi bir oluşturucuya birden çok kez atanabilir.</span><span class="sxs-lookup"><span data-stu-id="93d36-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="93d36-131">Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="93d36-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="93d36-132">Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olsa da, alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="93d36-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="93d36-133">Önceki örnekte, aşağıdaki örnek gibi bir deyim kullanırsanız:</span><span class="sxs-lookup"><span data-stu-id="93d36-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="93d36-134">derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="93d36-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="93d36-135">**Yalnızca okunan bir alan atanamıyor (bir oluşturucu veya değişken baş harfi hariç)**</span><span class="sxs-lookup"><span data-stu-id="93d36-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="93d36-136">Ref readonly dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="93d36-136">Ref readonly return example</span></span>

<span data-ttu-id="93d36-137">A'daki `readonly` değiştirici, döndürülen başvurunun değiştirilemediğini `ref return` gösterir.</span><span class="sxs-lookup"><span data-stu-id="93d36-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="93d36-138">Aşağıdaki örnek, kaynağına bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="93d36-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="93d36-139">Arayanların `readonly` kaynağı değiştiremediğini belirtmek için değiştirici kullanır:</span><span class="sxs-lookup"><span data-stu-id="93d36-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="93d36-140">Döndürülen tür bir `readonly struct`. olması gerekmez</span><span class="sxs-lookup"><span data-stu-id="93d36-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="93d36-141">Tarafından `ref` döndürülebilen herhangi bir tür `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="93d36-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="93d36-142">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="93d36-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="93d36-143">Ayrıca dil belirtimi önerilerini de görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93d36-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="93d36-144">readonly ref ve readonly struct</span><span class="sxs-lookup"><span data-stu-id="93d36-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="93d36-145">readonly struct üyeleri</span><span class="sxs-lookup"><span data-stu-id="93d36-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="93d36-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93d36-146">See also</span></span>

- [<span data-ttu-id="93d36-147">C# Referans</span><span class="sxs-lookup"><span data-stu-id="93d36-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="93d36-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="93d36-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="93d36-149">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="93d36-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="93d36-150">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="93d36-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="93d36-151">const</span><span class="sxs-lookup"><span data-stu-id="93d36-151">const</span></span>](const.md)
- [<span data-ttu-id="93d36-152">Alanlar</span><span class="sxs-lookup"><span data-stu-id="93d36-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
