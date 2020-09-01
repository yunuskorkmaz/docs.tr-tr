---
description: ReadOnly anahtar sözcüğü-C# başvurusu
title: ReadOnly anahtar sözcüğü-C# başvurusu
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b1bab5af18216fcef2162179493dbbb59e3470cf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137181"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="8d42d-103">readonly (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8d42d-103">readonly (C# Reference)</span></span>

<span data-ttu-id="8d42d-104">`readonly`Anahtar sözcüğü dört bağlamda kullanılabilecek bir değiştiricisidir:</span><span class="sxs-lookup"><span data-stu-id="8d42d-104">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="8d42d-105">Bir [alan bildiriminde](#readonly-field-example), `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-105">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="8d42d-106">Salt okunur bir alan, alan bildirimi ve Oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-106">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="8d42d-107">`readonly`Oluşturucu çıktıktan sonra bir alan atanamaz.</span><span class="sxs-lookup"><span data-stu-id="8d42d-107">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="8d42d-108">Bu kural, değer türleri ve başvuru türleri için farklı etkilere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8d42d-108">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="8d42d-109">Değer türleri doğrudan verilerini içerdiğinden, bir değer türü olan bir alan  `readonly` sabittir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-109">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="8d42d-110">Başvuru türleri, verilerine yönelik bir başvuru içerdiğinden, başvuru türü olan bir alan `readonly` her zaman aynı nesneye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d42d-110">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="8d42d-111">Bu nesne sabit değildir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-111">That object isn't immutable.</span></span> <span data-ttu-id="8d42d-112">`readonly`Değiştirici, alanın farklı bir başvuru türü örneğiyle değiştirilmesini önler.</span><span class="sxs-lookup"><span data-stu-id="8d42d-112">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="8d42d-113">Ancak, değiştirici alanın örnek verilerinin salt okunurdur alanı aracılığıyla değiştirilmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="8d42d-113">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="8d42d-114">Değişebilir bir başvuru türü olan bir dışarıdan görünür salt okunurdur alanı içeren dışarıdan görünen bir tür, bir güvenlik açığı olabilir ve uyarı [CA2104](/visualstudio/code-quality/ca2104) : "salt okuma kesilebilir başvuru türleri bildiremiyor" olarak tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-114">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="8d42d-115">Bir `readonly struct` tür tanımında, `readonly` yapı türünün sabit olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-115">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="8d42d-116">Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` struct](../builtin-types/struct.md#readonly-struct) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d42d-116">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="8d42d-117">Yapı türü içindeki bir örnek üye bildiriminde, bir `readonly` örnek üyesinin yapının durumunu değiştirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-117">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="8d42d-118">Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` örnek Üyeler](../builtin-types/struct.md#readonly-instance-members) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d42d-118">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="8d42d-119">Bir [ `ref readonly` Yöntem](#ref-readonly-return-example)döndürüldüğünde, `readonly` değiştirici yöntemin bir başvuru döndürdüğünü ve bu başvuruya yazma izni verilmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-119">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="8d42d-120">`readonly struct`Ve `ref readonly` bağlamları C# 7,2 ' ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-120">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="8d42d-121">`readonly` C# 8,0 ' de yapı üyeleri eklendi</span><span class="sxs-lookup"><span data-stu-id="8d42d-121">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="8d42d-122">ReadOnly alan örneği</span><span class="sxs-lookup"><span data-stu-id="8d42d-122">Readonly field example</span></span>

<span data-ttu-id="8d42d-123">Bu örnekte, alan değeri, `year` `ChangeYear` sınıf oluşturucusunda bir değer atanmış olsa da, yönteminde değiştirilemez:</span><span class="sxs-lookup"><span data-stu-id="8d42d-123">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="8d42d-124">Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d42d-124">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="8d42d-125">Bildirimde bir değişken başlatıldığında, örneğin:</span><span class="sxs-lookup"><span data-stu-id="8d42d-125">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="8d42d-126">Örnek alan bildirimini içeren sınıfın örnek oluşturucusunda.</span><span class="sxs-lookup"><span data-stu-id="8d42d-126">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="8d42d-127">Statik alan bildirimini içeren sınıfın statik oluşturucusunda.</span><span class="sxs-lookup"><span data-stu-id="8d42d-127">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="8d42d-128">Bu Oluşturucu bağlamları aynı zamanda bir `readonly` alanı [Out](out-parameter-modifier.md) veya [ref](ref.md) parametresi olarak geçirmek için geçerli olduğu tek bağlamlardır.</span><span class="sxs-lookup"><span data-stu-id="8d42d-128">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="8d42d-129">`readonly`Anahtar sözcüğü [const](const.md) anahtar sözcüğünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8d42d-129">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="8d42d-130">Bir `const` alan yalnızca alanın bildiriminde başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-130">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="8d42d-131">Alan `readonly` bildiriminde ve herhangi bir oluşturucuda bir alana birden çok kez atanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-131">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="8d42d-132">Bu nedenle, `readonly` alan, kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-132">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="8d42d-133">Ayrıca, bir `const` alan bir derleme zamanı sabiti olsa da, `readonly` Bu alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8d42d-133">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="8d42d-134">Yukarıdaki örnekte, aşağıdaki örnekte olduğu gibi bir ifade kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="8d42d-134">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="8d42d-135">Derleyici hata iletisini alırsınız:</span><span class="sxs-lookup"><span data-stu-id="8d42d-135">you'll get the compiler error message:</span></span>

<span data-ttu-id="8d42d-136">**Salt okunur bir alana atama yapılamaz (Oluşturucu veya değişken başlatıcı içinde olması dışında)**</span><span class="sxs-lookup"><span data-stu-id="8d42d-136">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="8d42d-137">Ref ReadOnly dönüş örneği</span><span class="sxs-lookup"><span data-stu-id="8d42d-137">Ref readonly return example</span></span>

<span data-ttu-id="8d42d-138">`readonly`Bir üzerinde değiştirici, `ref return` döndürülen başvurunun değiştirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d42d-138">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="8d42d-139">Aşağıdaki örnek, kaynağına bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="8d42d-139">The following example returns a reference to the origin.</span></span> <span data-ttu-id="8d42d-140">`readonly`Çağıranların kaynağı değiştiremeyeceğini belirtmek için değiştiricisini kullanır:</span><span class="sxs-lookup"><span data-stu-id="8d42d-140">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="8d42d-141">Döndürülen türün bir olması gerekmez `readonly struct` .</span><span class="sxs-lookup"><span data-stu-id="8d42d-141">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="8d42d-142">Tarafından döndürülebilecek herhangi bir tür `ref` tarafından döndürülebilecek `ref readonly` .</span><span class="sxs-lookup"><span data-stu-id="8d42d-142">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d42d-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8d42d-143">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="8d42d-144">Dil belirtimi tekliflerini de görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d42d-144">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="8d42d-145">ReadOnly ref ve ReadOnly yapısı</span><span class="sxs-lookup"><span data-stu-id="8d42d-145">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="8d42d-146">ReadOnly struct üyeleri</span><span class="sxs-lookup"><span data-stu-id="8d42d-146">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="8d42d-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d42d-147">See also</span></span>

- [<span data-ttu-id="8d42d-148">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8d42d-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d42d-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8d42d-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d42d-150">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8d42d-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d42d-151">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8d42d-151">Modifiers</span></span>](index.md)
- [<span data-ttu-id="8d42d-152">const</span><span class="sxs-lookup"><span data-stu-id="8d42d-152">const</span></span>](const.md)
- [<span data-ttu-id="8d42d-153">Alanlar</span><span class="sxs-lookup"><span data-stu-id="8d42d-153">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
