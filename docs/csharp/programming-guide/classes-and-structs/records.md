---
title: Kayıtlar-C# Programlama Kılavuzu
description: Kayıt türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: a45ed08da18e58f11793d6874d7275d9f5216be4
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260098"
---
# <a name="records-c-programming-guide"></a><span data-ttu-id="873a8-103">Kayıtlar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="873a8-103">Records (C# Programming Guide)</span></span>

<span data-ttu-id="873a8-104">[Kayıt](../../language-reference/builtin-types/record.md) , veri modelleriyle çalışma için özel sözdizimi ve davranış sağlayan bir [sınıftır](../../language-reference/keywords/class.md) .</span><span class="sxs-lookup"><span data-stu-id="873a8-104">A [record](../../language-reference/builtin-types/record.md) is a [class](../../language-reference/keywords/class.md) that provides special syntax and behavior for working with data models.</span></span> <span data-ttu-id="873a8-105">Sınıflar hakkında daha fazla bilgi için bkz. [sınıflar (C# Programlama Kılavuzu)](classes.md).</span><span class="sxs-lookup"><span data-stu-id="873a8-105">For information about classes, see [Classes (C# Programming Guide)](classes.md).</span></span>

## <a name="when-to-use-records"></a><span data-ttu-id="873a8-106">Kayıtlar ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="873a8-106">When to use records</span></span>

<span data-ttu-id="873a8-107">Aşağıdaki senaryolarda bir sınıfın yerine bir kayıt kullanmayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="873a8-107">Consider using a record in place of a class in the following scenarios:</span></span>

* <span data-ttu-id="873a8-108">Nesnelerin sabit olduğu bir başvuru türü tanımlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="873a8-108">You want to define a reference type for which objects are immutable.</span></span>
* <span data-ttu-id="873a8-109">[Değer eşitliğine](../statements-expressions-operators/equality-comparisons.md#value-equality)bağlı bir veri modeli tanımlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="873a8-109">You want to define a data model that depends on [value equality](../statements-expressions-operators/equality-comparisons.md#value-equality).</span></span>

### <a name="immutability"></a><span data-ttu-id="873a8-110">Değiştirilemezlik</span><span class="sxs-lookup"><span data-stu-id="873a8-110">Immutability</span></span>

<span data-ttu-id="873a8-111">Sabit bir tür, bir nesnenin örneği oluşturulduktan sonra herhangi bir özellik veya alan değerini değiştirmenize engel olur.</span><span class="sxs-lookup"><span data-stu-id="873a8-111">An immutable type is one that prevents you from changing any property or field values of an object after it's instantiated.</span></span> <span data-ttu-id="873a8-112">Bir tür iş parçacığı açısından güvenli olması gerektiğinde veya karma koda bir karma tabloya bağlı olduğunuzda, dengesde bilirlik yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="873a8-112">Immutability can be useful when you need a type to be thread-safe or you're depending on a hash code remaining the same in a hash table.</span></span> <span data-ttu-id="873a8-113">Kayıtlar, sabit türler oluşturmak ve bunlarla çalışmak için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="873a8-113">Records provide concise syntax for creating and working with immutable types.</span></span>

<span data-ttu-id="873a8-114">Tüm veri senaryoları için imlebilirlik kullanılabilirliği uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="873a8-114">Immutability isn't appropriate for all data scenarios.</span></span> <span data-ttu-id="873a8-115">Örneğin, [Entity Framework Core](/ef/core/), sabit varlık türleriyle güncellemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="873a8-115">[Entity Framework Core](/ef/core/), for example, doesn't support updating with immutable entity types.</span></span>

### <a name="value-equality"></a><span data-ttu-id="873a8-116">Değer eşitlik</span><span class="sxs-lookup"><span data-stu-id="873a8-116">Value equality</span></span>

<span data-ttu-id="873a8-117">Kayıtlar için, değer eşitliği, türlerin eşleşmesi ve tüm özellik ve alan değerleri eşleşiyorsa bir kayıt türünün iki değişkeninin eşit olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="873a8-117">For records, value equality means that two variables of a record type are equal if the types match and all property and field values match.</span></span> <span data-ttu-id="873a8-118">Sınıflar gibi diğer başvuru türleri için eşitlik, [başvuru eşitlik](../statements-expressions-operators/equality-comparisons.md#reference-equality)anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="873a8-118">For other reference types such as classes, equality means [reference equality](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span></span> <span data-ttu-id="873a8-119">Diğer bir deyişle, bir sınıf türünün iki değişkeni aynı nesneye başvurduklarında eşittir.</span><span class="sxs-lookup"><span data-stu-id="873a8-119">That is, two variables of a class type are equal if they refer to the same object.</span></span> <span data-ttu-id="873a8-120">İki kayıt örneğinin eşitlik düzeyini belirten Yöntemler ve işleçler değer eşitlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="873a8-120">Methods and operators that determine equality of two record instances use value equality.</span></span>

<span data-ttu-id="873a8-121">Tüm veri modelleri değer eşitliği ile iyi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="873a8-121">Not all data models work well with value equality.</span></span> <span data-ttu-id="873a8-122">Örneğin, [Entity Framework Core](/ef/core/) kavramsal bir varlık olan varlık türünün yalnızca bir örneğini kullandığından emin olmak için başvuru eşitliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="873a8-122">For example, [Entity Framework Core](/ef/core/) depends on reference equality to ensure that it uses only one instance of an entity type for what is conceptually one entity.</span></span> <span data-ttu-id="873a8-123">Bu nedenle, kayıt türleri Entity Framework Core varlık türleri olarak kullanım için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="873a8-123">For this reason, record types aren't appropriate for use as entity types in Entity Framework Core.</span></span>

## <a name="how-records-differ-from-classes"></a><span data-ttu-id="873a8-124">Kayıtların sınıflardan farkı</span><span class="sxs-lookup"><span data-stu-id="873a8-124">How records differ from classes</span></span>

<span data-ttu-id="873a8-125">Sınıfları [bildiren](classes.md#declaring-classes) ve [örnekleyen](classes.md#creating-objects) sözdizimi, kayıtlarla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="873a8-125">The same syntax that [declares](classes.md#declaring-classes) and [instantiates](classes.md#creating-objects) classes can be used with records.</span></span> <span data-ttu-id="873a8-126">Anahtar sözcüğünün anahtar sözcüğünü yerine koyun `record` `class` .</span><span class="sxs-lookup"><span data-stu-id="873a8-126">Just substitute the `record` keyword for the `class` keyword.</span></span> <span data-ttu-id="873a8-127">Benzer şekilde, devralma ilişkilerini ifade etmek için de aynı söz dizimi kayıtlar tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="873a8-127">Likewise, the same syntax for expressing inheritance relationships is supported by records.</span></span> <span data-ttu-id="873a8-128">Kayıtlar sınıflardan aşağıdaki yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="873a8-128">Records differ from classes in the following ways:</span></span>

* <span data-ttu-id="873a8-129">Sabit özelliklerle bir tür oluşturmak ve başlatmak için [konumsal parametreleri](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="873a8-129">You can use [positional parameters](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) to create and instantiate a type with immutable properties.</span></span>
* <span data-ttu-id="873a8-130">Sınıflarda başvuru eşitlik veya eşitsizlik belirten Yöntemler ve işleçler ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> ve gibi `==` ), kayıtlardaki [değer eşitlik veya eşitsizlik](../../language-reference/builtin-types/record.md#value-equality) olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="873a8-130">The same methods and operators that indicate reference equality or inequality in classes (such as <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> and `==`), indicate [value equality or inequality](../../language-reference/builtin-types/record.md#value-equality) in records.</span></span>
* <span data-ttu-id="873a8-131">Seçili özelliklerde yeni değerleri olan bir sabit nesnenin kopyasını oluşturmak için bir [ `with` ifade](../../language-reference/builtin-types/record.md#nondestructive-mutation) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="873a8-131">You can use a [`with` expression](../../language-reference/builtin-types/record.md#nondestructive-mutation) to create a copy of an immutable object with new values in selected properties.</span></span>
* <span data-ttu-id="873a8-132">Bir kaydın `ToString` yöntemi, bir nesnenin tür adını ve tüm ortak özelliklerinin adlarını ve değerlerini gösteren biçimli bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="873a8-132">A record's `ToString` method creates a formatted string that shows an object's type name and the names and values of all its public properties.</span></span>
* <span data-ttu-id="873a8-133">Bir kayıt, [başka bir kayıttan devralınabilir](../../language-reference/builtin-types/record.md#inheritance).</span><span class="sxs-lookup"><span data-stu-id="873a8-133">A record can [inherit from another record](../../language-reference/builtin-types/record.md#inheritance).</span></span> <span data-ttu-id="873a8-134">Bir kayıt bir sınıftan devralınabilir ve bir sınıf bir kayıttan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="873a8-134">A record can't inherit from a class, and a class can't inherit from a record.</span></span>

## <a name="examples"></a><span data-ttu-id="873a8-135">Örnekler</span><span class="sxs-lookup"><span data-stu-id="873a8-135">Examples</span></span>

<span data-ttu-id="873a8-136">Aşağıdaki örnek, bir kaydı bildirmek ve oluşturmak için Konumsal parametreleri kullanan bir ortak kayıt tanımlar.</span><span class="sxs-lookup"><span data-stu-id="873a8-136">The following example defines a public record that uses positional parameters to declare and instantiate a record.</span></span> <span data-ttu-id="873a8-137">Daha sonra tür adı ve özellik değerlerini yazdırır:</span><span class="sxs-lookup"><span data-stu-id="873a8-137">It then prints out the type name and property values:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

<span data-ttu-id="873a8-138">Aşağıdaki örnek kayıtlardaki değer eşitliğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="873a8-138">The following example demonstrates value equality in records:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

<span data-ttu-id="873a8-139">Aşağıdaki örnek, `with` değişmez bir nesneyi kopyalamak ve özelliklerden birini değiştirmek için bir ifadenin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="873a8-139">The following example demonstrates use of a `with` expression to copy an immutable object and change one of the properties:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

<span data-ttu-id="873a8-140">Daha fazla bilgi için bkz. [kayıtlar (C# Başvurusu)](../../language-reference/builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="873a8-140">For more information, see [Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="873a8-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="873a8-141">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="873a8-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="873a8-142">See also</span></span>

- [<span data-ttu-id="873a8-143">Sınıflar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="873a8-143">Classes (C# Programming Guide)</span></span>](classes.md)
- <span data-ttu-id="873a8-144">[Kayıtlar (C# Başvurusu)](../../language-reference/builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="873a8-144">[Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
- [<span data-ttu-id="873a8-145">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="873a8-145">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="873a8-146">Nesne odaklı programlama</span><span class="sxs-lookup"><span data-stu-id="873a8-146">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="873a8-147">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="873a8-147">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="873a8-148">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="873a8-148">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="873a8-149">Üyeler</span><span class="sxs-lookup"><span data-stu-id="873a8-149">Members</span></span>](members.md)
- [<span data-ttu-id="873a8-150">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="873a8-150">Methods</span></span>](methods.md)
- [<span data-ttu-id="873a8-151">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="873a8-151">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="873a8-152">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="873a8-152">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="873a8-153">Nesneler</span><span class="sxs-lookup"><span data-stu-id="873a8-153">Objects</span></span>](objects.md)
