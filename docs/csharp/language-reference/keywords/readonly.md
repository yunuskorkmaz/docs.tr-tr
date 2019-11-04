---
title: ReadOnly anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 30419200cfce785d7fcbbf59650241580a1f0ce4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454965"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="44ba9-102">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="44ba9-102">readonly (C# Reference)</span></span>

<span data-ttu-id="44ba9-103">`readonly` anahtar sözcüğü dört bağlamda kullanılabilecek bir değiştiricisidir:</span><span class="sxs-lookup"><span data-stu-id="44ba9-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="44ba9-104">[Alan bildiriminde](#readonly-field-example)`readonly`, alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="44ba9-105">Salt okunur bir alan, alan bildirimi ve Oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="44ba9-106">Oluşturucu çıktıktan sonra bir `readonly` alanı atanamaz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="44ba9-107">Bu kural, değer türleri ve başvuru türleri için farklı etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="44ba9-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="44ba9-108">Değer türleri doğrudan verilerini içerdiğinden, `readonly` değer türü olan bir alan sabittir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="44ba9-109">Başvuru türleri, verilerine yönelik bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alan her zaman aynı nesneye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44ba9-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="44ba9-110">Bu nesne sabit değildir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-110">That object isn't immutable.</span></span> <span data-ttu-id="44ba9-111">`readonly` değiştiricisi, alanın farklı bir başvuru türü örneğiyle değiştirilmesini önler.</span><span class="sxs-lookup"><span data-stu-id="44ba9-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="44ba9-112">Ancak, değiştirici alanın örnek verilerinin salt okunurdur alanı aracılığıyla değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="44ba9-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="44ba9-113">Değişebilir bir başvuru türü olan bir dışarıdan görünür salt okunurdur alanı içeren dışarıdan görünen bir tür, bir güvenlik açığı olabilir ve uyarı [CA2104](/visualstudio/code-quality/ca2104) : "salt okuma kesilebilir başvuru türleri bildiremiyor" olarak tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="44ba9-114">[`readonly struct` tanımında](#readonly-struct-example), `readonly` `struct` sabit olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="44ba9-115">[`readonly` üye tanımında](#readonly-member-examples), `readonly` bir `struct` üyesinin yapının iç durumunu muiçermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="44ba9-116">`ref readonly` bir [yöntemde döndürülen](#ref-readonly-return-example)`readonly` değiştirici, yöntemin bir başvuru döndürdüğünü ve bu başvuruya yazma izni bulunmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="44ba9-117">`readonly struct` ve `ref readonly` bağlamları 7,2 ' C# ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="44ba9-118">8,0 ' de C# `readonly` struct üyeleri eklendi</span><span class="sxs-lookup"><span data-stu-id="44ba9-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="44ba9-119">ReadOnly alan örneği</span><span class="sxs-lookup"><span data-stu-id="44ba9-119">Readonly field example</span></span>

<span data-ttu-id="44ba9-120">Bu örnekte, `year` alan değeri, sınıf oluşturucusunda bir değer atanmış olsa da, `ChangeYear`yönteminde değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="44ba9-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="44ba9-121">Bir `readonly` alanına yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ba9-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="44ba9-122">Bildirimde bir değişken başlatıldığında, örneğin:</span><span class="sxs-lookup"><span data-stu-id="44ba9-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="44ba9-123">Örnek alan bildirimini içeren sınıfın örnek oluşturucusunda.</span><span class="sxs-lookup"><span data-stu-id="44ba9-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="44ba9-124">Statik alan bildirimini içeren sınıfın statik oluşturucusunda.</span><span class="sxs-lookup"><span data-stu-id="44ba9-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="44ba9-125">Bu Oluşturucu bağlamları aynı zamanda bir `readonly` alanını [Out](out-parameter-modifier.md) veya [ref](ref.md) parametresi olarak geçirmek için geçerli olduğu tek bağlamlardır.</span><span class="sxs-lookup"><span data-stu-id="44ba9-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="44ba9-126">`readonly` anahtar sözcüğü [const](const.md) anahtar sözcüğünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="44ba9-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="44ba9-127">Bir `const` alanı yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="44ba9-128">`readonly` alan, alan bildiriminde ve herhangi bir oluşturucuda birden çok kez atanabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="44ba9-129">Bu nedenle, `readonly` alanlar kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="44ba9-130">Ayrıca, bir `const` alanı bir derleme zamanı sabiti olsa da, `readonly` alanı aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="44ba9-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="44ba9-131">Yukarıdaki örnekte, aşağıdaki örnekte olduğu gibi bir ifade kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="44ba9-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="44ba9-132">Derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="44ba9-132">you'll get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="44ba9-133">ReadOnly struct örneği</span><span class="sxs-lookup"><span data-stu-id="44ba9-133">Readonly struct example</span></span>

<span data-ttu-id="44ba9-134">`struct` tanımında `readonly` değiştiricisi yapının **sabit**olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-134">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="44ba9-135">Aşağıdaki örnekte gösterildiği gibi `struct` her örnek alanı `readonly`işaretlenmelidir:</span><span class="sxs-lookup"><span data-stu-id="44ba9-135">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="44ba9-136">Önceki örnek, depolama alanını bildirmek için [salt okunur otomatik özellikleri](../../properties.md#read-only) kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ba9-136">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="44ba9-137">Bu, derleyiciye bu özellikler için `readonly` yedekleme alanı oluşturmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="44ba9-137">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="44ba9-138">Ayrıca, `readonly` alanları doğrudan de bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ba9-138">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="44ba9-139">`readonly` işaretlenmemiş bir alan eklendiğinde `CS8340`derleyici hatası oluşturulur: "ReadOnly yapıların örnek alanları ReadOnly olmalıdır."</span><span class="sxs-lookup"><span data-stu-id="44ba9-139">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="44ba9-140">ReadOnly üye örnekleri</span><span class="sxs-lookup"><span data-stu-id="44ba9-140">Readonly member examples</span></span>

<span data-ttu-id="44ba9-141">Diğer zamanlarda, mutasyonu destekleyen bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-141">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="44ba9-142">Bu durumlarda, örnek üyelerinden birkaçı büyük olasılıkla yapının iç durumunu değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="44ba9-142">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="44ba9-143">Bu örnek üyelerini `readonly` değiştiricisiyle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-143">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="44ba9-144">Derleyici amacınızı zorluyor.</span><span class="sxs-lookup"><span data-stu-id="44ba9-144">The compiler enforces your intent.</span></span> <span data-ttu-id="44ba9-145">Bu üye, durumu doğrudan değiştirir veya `readonly` değiştiricisi ile de bildirilmeyen bir üyeye eriştiğinde sonuç, derleme zamanı hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="44ba9-145">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="44ba9-146">`readonly` değiştiricisi `class` veya `interface` üye bildirimlerinde değil `struct` üyelerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-146">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="44ba9-147">Geçerli `struct` yöntemlerine `readonly` değiştiricisini uygulayarak iki avantaja sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-147">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="44ba9-148">En önemlisi, derleyici amacınızı zorluyor.</span><span class="sxs-lookup"><span data-stu-id="44ba9-148">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="44ba9-149">Durumu değiştiren kod `readonly` yönteminde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-149">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="44ba9-150">Derleyici, performans iyileştirmelerini etkinleştirmek için `readonly` değiştiricisinden da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-150">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="44ba9-151">Büyük `struct` türleri `in` başvurusuyla geçirildiğinde, yapının durumu değiştirilemiyorsa derleyicinin bir savunma kopyası oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-151">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="44ba9-152">Yalnızca `readonly` üyelerine erişilirse, derleyici savunma kopyasını oluşturmayabilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-152">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="44ba9-153">`readonly` değiştiricisi, <xref:System.Object?displayProperty=nameWithType>tarafından belirtilen yöntemleri geçersiz kılan yöntemler de dahil olmak üzere `struct`çoğu üye üzerinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-153">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44ba9-154">Bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="44ba9-154">There are some restrictions:</span></span>

- <span data-ttu-id="44ba9-155">`readonly` statik üye bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-155">You can't declare `readonly` static members.</span></span>
- <span data-ttu-id="44ba9-156">`readonly` oluşturucuları bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-156">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="44ba9-157">`readonly` değiştiricisini bir özellik veya Dizin Oluşturucu bildirimine ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ba9-157">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="44ba9-158">`readonly` değiştiricisini bir özelliğin veya dizin oluşturucunun tek tek `get` veya `set` erişimcilerine de ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ba9-158">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="44ba9-159">`readonly` değiştiricisini hem özelliğe hem de aynı özelliğin erişimcilerine bir veya daha fazlasına ekleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-159">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="44ba9-160">Aynı kısıtlama, Dizin oluşturucular için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-160">That same restriction applies to indexers.</span></span>

<span data-ttu-id="44ba9-161">Derleyici, derleyicinin uyguladığı kodun durumu değiştirmediğinden otomatik uygulanan özelliklere `readonly` değiştiricisini örtülü olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="44ba9-161">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="44ba9-162">Aşağıdaki bildirimlerle eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="44ba9-162">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="44ba9-163">`readonly` değiştiricisini bu konumlara ekleyebilirsiniz, ancak anlamlı bir etkiye sahip olmaz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-163">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="44ba9-164">`readonly` değiştiricisini otomatik uygulanan bir özellik ayarlayıcısına veya okuma/yazma otomatik uygulanan özelliğine ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-164">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="44ba9-165">Ref ReadOnly dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="44ba9-165">Ref readonly return example</span></span>

<span data-ttu-id="44ba9-166">`ref return` `readonly` değiştiricisi döndürülen başvurunun değiştirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-166">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="44ba9-167">Aşağıdaki örnek, kaynağına bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="44ba9-167">The following example returns a reference to the origin.</span></span> <span data-ttu-id="44ba9-168">Çağıranların kaynağı değiştiremeyeceğini belirtmek için `readonly` değiştiricisini kullanır:</span><span class="sxs-lookup"><span data-stu-id="44ba9-168">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="44ba9-169">Döndürülen türün bir `readonly struct`olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="44ba9-169">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="44ba9-170">`ref` tarafından döndürülebilecek herhangi bir tür, `ref readonly`tarafından döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="44ba9-170">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="44ba9-171">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="44ba9-171">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="44ba9-172">Dil belirtimi tekliflerini de görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="44ba9-172">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="44ba9-173">ReadOnly ref ve ReadOnly yapısı</span><span class="sxs-lookup"><span data-stu-id="44ba9-173">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="44ba9-174">ReadOnly struct üyeleri</span><span class="sxs-lookup"><span data-stu-id="44ba9-174">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="44ba9-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44ba9-175">See also</span></span>

- [<span data-ttu-id="44ba9-176">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="44ba9-176">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="44ba9-177">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="44ba9-177">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="44ba9-178">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="44ba9-178">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="44ba9-179">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="44ba9-179">Modifiers</span></span>](index.md)
- [<span data-ttu-id="44ba9-180">const</span><span class="sxs-lookup"><span data-stu-id="44ba9-180">const</span></span>](const.md)
- [<span data-ttu-id="44ba9-181">Alanlar</span><span class="sxs-lookup"><span data-stu-id="44ba9-181">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
