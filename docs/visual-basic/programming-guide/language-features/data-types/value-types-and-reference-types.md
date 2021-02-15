---
description: 'Daha fazla bilgi edinin: değer türleri ve başvuru türleri'
title: Değer Türleri ve Başvuru Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 22cce68260955545e810f6fefe645b5ad6a37ca5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462145"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="99f0e-103">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-103">Value Types and Reference Types</span></span>

<span data-ttu-id="99f0e-104">Visual Basic iki tür tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="99f0e-104">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="99f0e-105">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="99f0e-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="99f0e-106">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="99f0e-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="99f0e-107">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişken üzerindeki işlemler diğerini etkileme ( [parametrelerde ByRef değiştirici](../../../language-reference/modifiers/byref.md)olması dışında) mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="99f0e-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="99f0e-108">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-108">Value Types</span></span>  

 <span data-ttu-id="99f0e-109">Veri türü, verileri kendi bellek ayırması içinde tutuyorsa bir *değer türüdür* .</span><span class="sxs-lookup"><span data-stu-id="99f0e-109">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="99f0e-110">Değer türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="99f0e-110">Value types include the following:</span></span>  
  
- <span data-ttu-id="99f0e-111">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-111">All numeric data types</span></span>  
  
- <span data-ttu-id="99f0e-112">`Boolean`, `Char` ve `Date`</span><span class="sxs-lookup"><span data-stu-id="99f0e-112">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="99f0e-113">Üyeleri başvuru türleri olsa bile tüm yapılar</span><span class="sxs-lookup"><span data-stu-id="99f0e-113">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="99f0e-114">Numaralandırmalar, temel alınan türü her zaman,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` , veya `ULong`</span><span class="sxs-lookup"><span data-stu-id="99f0e-114">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="99f0e-115">Her yapı, başvuru türü üyeleri içerse de bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="99f0e-115">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="99f0e-116">Bu nedenle, ve gibi değer türleri `Char` `Integer` .NET Framework yapılar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99f0e-116">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="99f0e-117">Ayrılmış anahtar sözcüğünü kullanarak bir değer türü bildirebilirsiniz, örneğin, `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="99f0e-117">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="99f0e-118">`New`Anahtar sözcüğünü bir değer türünü başlatmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99f0e-118">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="99f0e-119">Bu özellikle, türün parametreleri alan bir Oluşturucusu varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="99f0e-119">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="99f0e-120">Bu, <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> sağlanan bölümlerden yeni bir değer oluşturan Oluşturucu örneğidir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="99f0e-120">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="99f0e-121">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-121">Reference Types</span></span>  

 <span data-ttu-id="99f0e-122">Bir *başvuru türü* , verilerine bir başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="99f0e-122">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="99f0e-123">Başvuru türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="99f0e-123">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="99f0e-124">Tüm diziler, öğeleri değer türseler bile</span><span class="sxs-lookup"><span data-stu-id="99f0e-124">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="99f0e-125">Gibi sınıf türleri <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="99f0e-125">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="99f0e-126">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="99f0e-126">Delegates</span></span>  
  
 <span data-ttu-id="99f0e-127">Sınıf bir *başvuru türüdür*.</span><span class="sxs-lookup"><span data-stu-id="99f0e-127">A class is a *reference type*.</span></span> <span data-ttu-id="99f0e-128">Her dizi, üyeleri değer türleri olsa bile bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="99f0e-128">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="99f0e-129">Her başvuru türü temeldeki bir .NET Framework sınıfını temsil ettiğinden, onu başlattığınızda [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99f0e-129">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="99f0e-130">Aşağıdaki ifade bir diziyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="99f0e-130">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="99f0e-131">Türler olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="99f0e-131">Elements That Are Not Types</span></span>  

 <span data-ttu-id="99f0e-132">Aşağıdaki programlama öğeleri tür olarak nitelemez, çünkü bunlardan herhangi birini tanımlanmış bir öğe için veri türü olarak belirtemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="99f0e-132">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="99f0e-133">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="99f0e-133">Namespaces</span></span>  
  
- <span data-ttu-id="99f0e-134">Modüller</span><span class="sxs-lookup"><span data-stu-id="99f0e-134">Modules</span></span>  
  
- <span data-ttu-id="99f0e-135">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="99f0e-135">Events</span></span>  
  
- <span data-ttu-id="99f0e-136">Özellikler ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="99f0e-136">Properties and procedures</span></span>  
  
- <span data-ttu-id="99f0e-137">Değişkenler, sabitler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="99f0e-137">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="99f0e-138">Nesne veri türüyle çalışma</span><span class="sxs-lookup"><span data-stu-id="99f0e-138">Working with the Object Data Type</span></span>  

 <span data-ttu-id="99f0e-139">Veri türü değişkenine bir başvuru türü veya değer türü atayabilirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="99f0e-139">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="99f0e-140">Değişken, hiçbir zaman verilerin `Object` kendisi olan bir başvuruya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99f0e-140">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="99f0e-141">Ancak, bir değişkene bir değer türü atarsanız `Object` , kendi verilerini tutan gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="99f0e-141">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="99f0e-142">Daha fazla bilgi için bkz. [nesne veri türü](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="99f0e-142">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="99f0e-143">Bir `Object` değişkenin bir başvuru türü olarak hareket ettiğini veya bir değer türünün, <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> ad alanının sınıfındaki yöntemine geçirerek bir değer türü olup olmadığını görebilirsiniz <xref:Microsoft.VisualBasic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="99f0e-143">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="99f0e-144"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True` `Object` değişkenin içeriği bir başvuru türünü temsil ediyorsa, döndürür.</span><span class="sxs-lookup"><span data-stu-id="99f0e-144"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f0e-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f0e-145">See also</span></span>

- [<span data-ttu-id="99f0e-146">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-146">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="99f0e-147">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-147">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="99f0e-148">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="99f0e-148">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="99f0e-149">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="99f0e-149">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="99f0e-150">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="99f0e-150">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="99f0e-151">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="99f0e-151">Data Types</span></span>](index.md)
