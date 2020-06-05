---
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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392980"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="4c5ca-102">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-102">Value Types and Reference Types</span></span>
<span data-ttu-id="4c5ca-103">Visual Basic iki tür tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="4c5ca-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="4c5ca-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="4c5ca-106">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişken üzerindeki işlemler diğerini etkileme ( [parametrelerde ByRef değiştirici](../../../language-reference/modifiers/byref.md)olması dışında) mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="4c5ca-107">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-107">Value Types</span></span>  
 <span data-ttu-id="4c5ca-108">Veri türü, verileri kendi bellek ayırması içinde tutuyorsa bir *değer türüdür* .</span><span class="sxs-lookup"><span data-stu-id="4c5ca-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="4c5ca-109">Değer türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="4c5ca-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="4c5ca-110">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-110">All numeric data types</span></span>  
  
- <span data-ttu-id="4c5ca-111">`Boolean`, `Char` ve`Date`</span><span class="sxs-lookup"><span data-stu-id="4c5ca-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="4c5ca-112">Üyeleri başvuru türleri olsa bile tüm yapılar</span><span class="sxs-lookup"><span data-stu-id="4c5ca-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="4c5ca-113">Numaralandırmalar, temel alınan türü her zaman,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` , veya`ULong`</span><span class="sxs-lookup"><span data-stu-id="4c5ca-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="4c5ca-114">Her yapı, başvuru türü üyeleri içerse de bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="4c5ca-115">Bu nedenle, ve gibi değer türleri `Char` `Integer` .NET Framework yapılar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="4c5ca-116">Ayrılmış anahtar sözcüğünü kullanarak bir değer türü bildirebilirsiniz, örneğin, `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="4c5ca-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="4c5ca-117">`New`Anahtar sözcüğünü bir değer türünü başlatmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="4c5ca-118">Bu özellikle, türün parametreleri alan bir Oluşturucusu varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="4c5ca-119">Bu, <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> sağlanan bölümlerden yeni bir değer oluşturan Oluşturucu örneğidir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="4c5ca-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="4c5ca-120">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-120">Reference Types</span></span>  
 <span data-ttu-id="4c5ca-121">Bir *başvuru türü* , verilerine bir başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="4c5ca-122">Başvuru türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="4c5ca-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="4c5ca-123">Tüm diziler, öğeleri değer türseler bile</span><span class="sxs-lookup"><span data-stu-id="4c5ca-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="4c5ca-124">Gibi sınıf türleri<xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="4c5ca-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="4c5ca-125">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="4c5ca-125">Delegates</span></span>  
  
 <span data-ttu-id="4c5ca-126">Sınıf bir *başvuru türüdür*.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-126">A class is a *reference type*.</span></span> <span data-ttu-id="4c5ca-127">Her dizi, üyeleri değer türleri olsa bile bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="4c5ca-128">Her başvuru türü temeldeki bir .NET Framework sınıfını temsil ettiğinden, onu başlattığınızda [New Operator](../../../language-reference/operators/new-operator.md) anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="4c5ca-129">Aşağıdaki ifade bir diziyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="4c5ca-130">Türler olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="4c5ca-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="4c5ca-131">Aşağıdaki programlama öğeleri tür olarak nitelemez, çünkü bunlardan herhangi birini tanımlanmış bir öğe için veri türü olarak belirtemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c5ca-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="4c5ca-132">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="4c5ca-132">Namespaces</span></span>  
  
- <span data-ttu-id="4c5ca-133">Modül</span><span class="sxs-lookup"><span data-stu-id="4c5ca-133">Modules</span></span>  
  
- <span data-ttu-id="4c5ca-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4c5ca-134">Events</span></span>  
  
- <span data-ttu-id="4c5ca-135">Özellikler ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="4c5ca-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="4c5ca-136">Değişkenler, sabitler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="4c5ca-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="4c5ca-137">Nesne veri türüyle çalışma</span><span class="sxs-lookup"><span data-stu-id="4c5ca-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="4c5ca-138">Veri türü değişkenine bir başvuru türü veya değer türü atayabilirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="4c5ca-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="4c5ca-139">Değişken, hiçbir zaman verilerin `Object` kendisi olan bir başvuruya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="4c5ca-140">Ancak, bir değişkene bir değer türü atarsanız `Object` , kendi verilerini tutan gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="4c5ca-141">Daha fazla bilgi için bkz. [nesne veri türü](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="4c5ca-141">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="4c5ca-142">Bir `Object` değişkenin bir başvuru türü olarak hareket ettiğini veya bir değer türünün, <xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information> ad alanının sınıfındaki yöntemine geçirerek bir değer türü olup olmadığını görebilirsiniz <xref:Microsoft.VisualBasic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4c5ca-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4c5ca-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>`True` `Object` değişkenin içeriği bir başvuru türünü temsil ediyorsa, döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5ca-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c5ca-144">See also</span></span>

- [<span data-ttu-id="4c5ca-145">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-145">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="4c5ca-146">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-146">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="4c5ca-147">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="4c5ca-147">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4c5ca-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="4c5ca-148">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="4c5ca-149">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="4c5ca-149">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="4c5ca-150">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="4c5ca-150">Data Types</span></span>](index.md)
