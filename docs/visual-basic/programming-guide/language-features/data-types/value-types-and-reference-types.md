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
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582640"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="8e0ed-102">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-102">Value Types and Reference Types</span></span>
<span data-ttu-id="8e0ed-103">Visual Basic iki tür tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="8e0ed-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="8e0ed-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="8e0ed-106">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişken üzerindeki işlemler diğerini etkileme ( [parametrelerde ByRef değiştirici](../../../language-reference/modifiers/byref.md)olması dışında) mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="8e0ed-107">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-107">Value Types</span></span>  
 <span data-ttu-id="8e0ed-108">Veri türü, verileri kendi bellek ayırması içinde tutuyorsa bir *değer türüdür* .</span><span class="sxs-lookup"><span data-stu-id="8e0ed-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="8e0ed-109">Değer türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8e0ed-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="8e0ed-110">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-110">All numeric data types</span></span>  
  
- <span data-ttu-id="8e0ed-111">`Boolean`, `Char` ve `Date`</span><span class="sxs-lookup"><span data-stu-id="8e0ed-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="8e0ed-112">Üyeleri başvuru türleri olsa bile tüm yapılar</span><span class="sxs-lookup"><span data-stu-id="8e0ed-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="8e0ed-113">Numaralandırmalar, temel alınan türü her zaman `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` veya `ULong`</span><span class="sxs-lookup"><span data-stu-id="8e0ed-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="8e0ed-114">Her yapı, başvuru türü üyeleri içerse de bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="8e0ed-115">Bu nedenle, `Char` ve `Integer` gibi değer türleri .NET Framework yapıları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="8e0ed-116">Ayrılmış anahtar sözcüğünü kullanarak bir değer türü bildirebilirsiniz, örneğin, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="8e0ed-117">Değer türünü başlatmak için `New` anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="8e0ed-118">Bu özellikle, türün parametreleri alan bir Oluşturucusu varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="8e0ed-119">Bunun bir örneği, sağlanan bölümlerden yeni bir `Decimal` değeri oluşturan <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> oluşturucusudur.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="8e0ed-120">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-120">Reference Types</span></span>  
 <span data-ttu-id="8e0ed-121">Bir *başvuru türü* , verilerine bir başvuru depolar.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="8e0ed-122">Başvuru türleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8e0ed-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="8e0ed-123">Tüm diziler, öğeleri değer türseler bile</span><span class="sxs-lookup"><span data-stu-id="8e0ed-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="8e0ed-124">@No__t_0 gibi sınıf türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="8e0ed-125">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="8e0ed-125">Delegates</span></span>  
  
 <span data-ttu-id="8e0ed-126">Sınıf bir *başvuru türüdür*.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-126">A class is a *reference type*.</span></span> <span data-ttu-id="8e0ed-127">Her dizi, üyeleri değer türleri olsa bile bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="8e0ed-128">Her başvuru türü temeldeki bir .NET Framework sınıfını temsil ettiğinden, onu başlattığınızda [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="8e0ed-129">Aşağıdaki ifade bir diziyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="8e0ed-130">Türler olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="8e0ed-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="8e0ed-131">Aşağıdaki programlama öğeleri tür olarak nitelemez, çünkü bunlardan herhangi birini tanımlanmış bir öğe için veri türü olarak belirtemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e0ed-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="8e0ed-132">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="8e0ed-132">Namespaces</span></span>  
  
- <span data-ttu-id="8e0ed-133">Modüller</span><span class="sxs-lookup"><span data-stu-id="8e0ed-133">Modules</span></span>  
  
- <span data-ttu-id="8e0ed-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8e0ed-134">Events</span></span>  
  
- <span data-ttu-id="8e0ed-135">Özellikler ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="8e0ed-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="8e0ed-136">Değişkenler, sabitler ve alanlar</span><span class="sxs-lookup"><span data-stu-id="8e0ed-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="8e0ed-137">Nesne veri türüyle çalışma</span><span class="sxs-lookup"><span data-stu-id="8e0ed-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="8e0ed-138">@No__t_0 veri türü değişkenine bir başvuru türü veya değer türü atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="8e0ed-139">Bir `Object` değişken her zaman veriye bir başvuru barındırır, hiçbir zaman verilerin kendisi değildir.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="8e0ed-140">Ancak, bir `Object` değişkenine bir değer türü atarsanız, kendi verilerini tutan gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="8e0ed-141">Daha fazla bilgi için bkz. [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8e0ed-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="8e0ed-142">Bir `Object` değişkeninin, <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanının <xref:Microsoft.VisualBasic.Information> sınıfındaki <xref:Microsoft.VisualBasic.Information.IsReference%2A> yöntemine geçirerek bir başvuru türü veya değer türü olarak davranıp davranmadığını fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8e0ed-143">`Object` değişkeninin içeriği bir başvuru türünü temsil ediyorsa <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0ed-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e0ed-144">See also</span></span>

- [<span data-ttu-id="8e0ed-145">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="8e0ed-146">Visual Basic dönüşümler yazın</span><span class="sxs-lookup"><span data-stu-id="8e0ed-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="8e0ed-147">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="8e0ed-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="8e0ed-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="8e0ed-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="8e0ed-149">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8e0ed-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="8e0ed-150">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8e0ed-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
