---
title: readonly anahtar kelime - C# Başvuru
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345143"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="28b46-102">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28b46-102">readonly (C# Reference)</span></span>

<span data-ttu-id="28b46-103">Anahtar `readonly` kelime, dört bağlamda kullanılabilen bir değiştiricidir:</span><span class="sxs-lookup"><span data-stu-id="28b46-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="28b46-104">Alan [bildiriminde,](#readonly-field-example) `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="28b46-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="28b46-105">Yalnızca okunan bir alan, alan bildirimi ve oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="28b46-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="28b46-106">Bir `readonly` alan, yapıcı çıktıktan sonra atanamaz.</span><span class="sxs-lookup"><span data-stu-id="28b46-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="28b46-107">Bu kuralın değer türleri ve başvuru türleri için farklı etkileri vardır:</span><span class="sxs-lookup"><span data-stu-id="28b46-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="28b46-108">Değer türleri doğrudan verilerini içerdiğinden, değer `readonly` türü olan bir alan değişmez.</span><span class="sxs-lookup"><span data-stu-id="28b46-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="28b46-109">Başvuru türleri verilerine bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alanın her zaman aynı nesneye başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28b46-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="28b46-110">Bu nesne değişmez değil.</span><span class="sxs-lookup"><span data-stu-id="28b46-110">That object isn't immutable.</span></span> <span data-ttu-id="28b46-111">Değiştirici, `readonly` alanın başvuru türünün farklı bir örneğiyle değiştirilmesini önler.</span><span class="sxs-lookup"><span data-stu-id="28b46-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="28b46-112">Ancak, değiştirici, alanın örnek verilerinin salt okunur alanı boyunca değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="28b46-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="28b46-113">Mutable başvuru türü olan harici olarak görünür salt okunur alan içeren harici olarak görünen bir tür bir güvenlik açığı olabilir ve [ca2104](/visualstudio/code-quality/ca2104) uyarısını tetikleyebilir: "Yalnızca mutable başvuru türlerini okumayı bildirin."</span><span class="sxs-lookup"><span data-stu-id="28b46-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="28b46-114">Bir `readonly struct` tür tanımında, `readonly` yapı türünün değişmez olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="28b46-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="28b46-115">Daha fazla bilgi [ `readonly` ](../builtin-types/struct.md#readonly-struct) için Yapı [türleri](../builtin-types/struct.md) makalesinin yapı bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="28b46-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="28b46-116">[ `readonly` Üye](#readonly-member-examples)tanımında, `readonly` bir `struct` üyenin yapının iç durumunu mutasyona uğratmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="28b46-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="28b46-117">Yöntem [ `ref readonly` dönüşünde,](#ref-readonly-return-example) `readonly` değiştirici yöntemin bir başvurudöndürür ve bu başvuru için yazı izin verilmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="28b46-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="28b46-118">Ve `readonly struct` `ref readonly` bağlamlar C# 7.2'ye eklendi.</span><span class="sxs-lookup"><span data-stu-id="28b46-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="28b46-119">`readonly`yapı üyeleri C# 8.0'a eklendi</span><span class="sxs-lookup"><span data-stu-id="28b46-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="28b46-120">Readonly alan örneği</span><span class="sxs-lookup"><span data-stu-id="28b46-120">Readonly field example</span></span>

<span data-ttu-id="28b46-121">Bu örnekte, sınıf oluşturucuya bir değer atanmış `ChangeYear`olsa bile, yöntemde alanın `year` değeri değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="28b46-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="28b46-122">Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28b46-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="28b46-123">Değişken bildirimde başharfe geçtiğinde, örneğin:</span><span class="sxs-lookup"><span data-stu-id="28b46-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="28b46-124">Örnek alan bildirimini içeren sınıfın bir örnek oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="28b46-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="28b46-125">Statik alan bildirimini içeren sınıfın statik oluşturucuda.</span><span class="sxs-lookup"><span data-stu-id="28b46-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="28b46-126">Bu oluşturucu bağlamlar, bir `readonly` alanı dış [veya](out-parameter-modifier.md) [ref](ref.md) parametresi olarak geçirmenin geçerli olduğu tek bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="28b46-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="28b46-127">Anahtar `readonly` kelime [const](const.md) anahtar kelime farklıdır.</span><span class="sxs-lookup"><span data-stu-id="28b46-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="28b46-128">Bir `const` alan yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="28b46-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="28b46-129">Alan `readonly` bildiriminde ve herhangi bir oluşturucuya birden çok kez atanabilir.</span><span class="sxs-lookup"><span data-stu-id="28b46-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="28b46-130">Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="28b46-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="28b46-131">Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olsa da, alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="28b46-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="28b46-132">Önceki örnekte, aşağıdaki örnek gibi bir deyim kullanırsanız:</span><span class="sxs-lookup"><span data-stu-id="28b46-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="28b46-133">derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="28b46-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="28b46-134">**Yalnızca okunan bir alan atanamıyor (bir oluşturucu veya değişken baş harfi hariç)**</span><span class="sxs-lookup"><span data-stu-id="28b46-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="28b46-135">Readonly üye örnekleri</span><span class="sxs-lookup"><span data-stu-id="28b46-135">Readonly member examples</span></span>

<span data-ttu-id="28b46-136">Diğer zamanlarda, mutasyonu destekleyen bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="28b46-137">Bu gibi durumlarda, örnek üyelerden bazıları büyük olasılıkla yapının iç durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="28b46-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="28b46-138">Bu örnek üyeleri `readonly` değiştirici ile bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="28b46-139">Derleyici niyetinizi zorlar.</span><span class="sxs-lookup"><span data-stu-id="28b46-139">The compiler enforces your intent.</span></span> <span data-ttu-id="28b46-140">Bu üye durumu doğrudan değiştirirse veya `readonly` değiştiriciile birlikte bildirilmemiş bir üyeye erişirse, sonuç derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="28b46-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="28b46-141">Değiştirici üyeler `struct` için geçerlidir, `class` `interface` üye beyannamelerinde veya üye beyanlarında geçerli değildir. `readonly`</span><span class="sxs-lookup"><span data-stu-id="28b46-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="28b46-142">`readonly` Değiştiriciyi geçerli `struct` yöntemlere uygulayarak iki avantaj elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="28b46-143">En önemlisi, derleyici niyetinizi zorlar.</span><span class="sxs-lookup"><span data-stu-id="28b46-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="28b46-144">Durumu değiştiren kod bir `readonly` yöntemde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="28b46-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="28b46-145">Derleyici, performans optimizasyonlarını `readonly` etkinleştirmek için değiştiriciden de yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="28b46-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="28b46-146">Büyük `struct` türler başvuru `in` yla geçirildiğinde, yapının durumu değiştirilse derleyicinin bir savunma kopyası oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28b46-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="28b46-147">Yalnızca `readonly` üyelere erişilirse, derleyici savunma kopyasını oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="28b46-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="28b46-148">`readonly` Değiştirici, 'de <xref:System.Object?displayProperty=nameWithType>bildirilen yöntemleri geçersiz kılma yöntemleri de dahil olmak üzere, bir `struct`üyenin çoğu üzerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="28b46-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28b46-149">Bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="28b46-149">There are some restrictions:</span></span>

- <span data-ttu-id="28b46-150">Statik yöntemleri veya `readonly` özellikleri bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="28b46-151">Yapıcıları beyan `readonly` edemezsin.</span><span class="sxs-lookup"><span data-stu-id="28b46-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="28b46-152">`readonly` Değiştiriciyi bir özellik veya dizinleyici bildirimine ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28b46-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="28b46-153">`readonly` Değiştiriciyi bir özellik veya `get` dizinleyicinin tek tek veya `set` erişimine de ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28b46-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="28b46-154">`readonly` Değiştiriciyi hem bir özelliğe hem de aynı özelliğin erişimine bir veya daha fazla sınayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="28b46-155">Aynı kısıtlama dizinleyiciler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="28b46-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="28b46-156">Derleyici, derleyicinin `readonly` uygulanan kodun durumu değiştirmediği otomatik olarak uygulanan özelliklere dolaylı olarak değiştirici uygular.</span><span class="sxs-lookup"><span data-stu-id="28b46-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="28b46-157">Aşağıdaki beyanlara eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="28b46-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="28b46-158">Bu konumlara `readonly` değiştirici ekleyebilirsiniz, ancak anlamlı bir etkisi olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="28b46-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="28b46-159">`readonly` Değiştiriciyi otomatik olarak uygulanan bir özellik ayarlayıcısına veya otomatik olarak uygulanan bir özelliği okuma/yazma özelliğine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28b46-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="28b46-160">Ref readonly dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="28b46-160">Ref readonly return example</span></span>

<span data-ttu-id="28b46-161">A'daki `readonly` değiştirici, döndürülen başvurunun değiştirilemediğini `ref return` gösterir.</span><span class="sxs-lookup"><span data-stu-id="28b46-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="28b46-162">Aşağıdaki örnek, kaynağına bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="28b46-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="28b46-163">Arayanların `readonly` kaynağı değiştiremediğini belirtmek için değiştirici kullanır:</span><span class="sxs-lookup"><span data-stu-id="28b46-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="28b46-164">Döndürülen tür bir `readonly struct`. olması gerekmez</span><span class="sxs-lookup"><span data-stu-id="28b46-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="28b46-165">Tarafından `ref` döndürülebilen herhangi bir tür `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="28b46-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="28b46-166">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="28b46-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="28b46-167">Ayrıca dil belirtimi önerilerini de görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28b46-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="28b46-168">readonly ref ve readonly struct</span><span class="sxs-lookup"><span data-stu-id="28b46-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="28b46-169">readonly struct üyeleri</span><span class="sxs-lookup"><span data-stu-id="28b46-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="28b46-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28b46-170">See also</span></span>

- [<span data-ttu-id="28b46-171">C# Referans</span><span class="sxs-lookup"><span data-stu-id="28b46-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28b46-172">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28b46-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="28b46-173">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="28b46-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="28b46-174">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="28b46-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="28b46-175">const</span><span class="sxs-lookup"><span data-stu-id="28b46-175">const</span></span>](const.md)
- [<span data-ttu-id="28b46-176">Alanlar</span><span class="sxs-lookup"><span data-stu-id="28b46-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
