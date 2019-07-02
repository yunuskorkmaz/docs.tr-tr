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
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504884"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="fd642-102">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-102">Value Types and Reference Types</span></span>
<span data-ttu-id="fd642-103">Visual Basic'te tür iki tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="fd642-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="fd642-104">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="fd642-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="fd642-105">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="fd642-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="fd642-106">Değer türleri ile her değişkenin kendi veri kopyası vardır ve yapılan işlemlerin diğerini etkilemesi için bir değişken üzerinde değil (dışındaki durumunda [parametreleri ByRef değiştiricisi](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="fd642-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="fd642-107">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-107">Value Types</span></span>  
 <span data-ttu-id="fd642-108">Bir veri türü olan bir *değer türü* kendi bellek ayırma verileri tutuyorsa.</span><span class="sxs-lookup"><span data-stu-id="fd642-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="fd642-109">Değer türleri aşağıdakileri kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="fd642-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="fd642-110">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-110">All numeric data types</span></span>  
  
- <span data-ttu-id="fd642-111">`Boolean`, `Char`, ve `Date`</span><span class="sxs-lookup"><span data-stu-id="fd642-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="fd642-112">Başvuru türleri üyelerinin olması durumunda bile tüm yapıları</span><span class="sxs-lookup"><span data-stu-id="fd642-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="fd642-113">Her zaman kendi temel türü olduğundan numaralandırmalar `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, veya `ULong`</span><span class="sxs-lookup"><span data-stu-id="fd642-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="fd642-114">Başvuru türü üyeleri içeren olsa bile her bir değer türü yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="fd642-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="fd642-115">Bu nedenle, değer türleri gibi `Char` ve `Integer` .NET Framework yapıları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fd642-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="fd642-116">Ayrılmış anahtar sözcüğü, örneğin,'ı kullanarak bir değer türü bildirebilirsiniz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fd642-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="fd642-117">Ayrıca `New` anahtar sözcüğü, bir değer türü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="fd642-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="fd642-118">Tür parametreleri alan bir oluşturucu sahipse, bu özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="fd642-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="fd642-119">Bunun bir örneği <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> yeni bir derleme Oluşturucu `Decimal` sağlanan parçalarından değeri.</span><span class="sxs-lookup"><span data-stu-id="fd642-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="fd642-120">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-120">Reference Types</span></span>  
 <span data-ttu-id="fd642-121">A *başvuru türüne* başvuru verilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="fd642-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="fd642-122">Başvuru türleri aşağıdakileri kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="fd642-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="fd642-123">Tüm diziler, kendi öğeleri değer türleri olsa bile</span><span class="sxs-lookup"><span data-stu-id="fd642-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="fd642-124">Sınıfı, gibi türleri <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="fd642-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="fd642-125">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="fd642-125">Delegates</span></span>  
  
 <span data-ttu-id="fd642-126">Bir sınıf bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="fd642-126">A class is a *reference type*.</span></span> <span data-ttu-id="fd642-127">Üyeleri, değer türleri olsa bile, her dizide bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fd642-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="fd642-128">Her bir başvuru türü temel alınan bir .NET Framework sınıfı temsil eder. bu yana kullanmalısınız [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) başlattığınızda, anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fd642-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="fd642-129">Aşağıdaki deyim, bir dizi başlatır.</span><span class="sxs-lookup"><span data-stu-id="fd642-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="fd642-130">Türleri öğeleri</span><span class="sxs-lookup"><span data-stu-id="fd642-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="fd642-131">Bunların hiçbirine olarak bildirilen bir öğe için bir veri türü belirtilemez çünkü aşağıdaki programlama öğeleri türleri olarak nitelendirmeyin:</span><span class="sxs-lookup"><span data-stu-id="fd642-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="fd642-132">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="fd642-132">Namespaces</span></span>  
  
- <span data-ttu-id="fd642-133">Modüller</span><span class="sxs-lookup"><span data-stu-id="fd642-133">Modules</span></span>  
  
- <span data-ttu-id="fd642-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="fd642-134">Events</span></span>  
  
- <span data-ttu-id="fd642-135">Özellikler ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="fd642-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="fd642-136">Değişkenleri, sabitleri ve alanlar</span><span class="sxs-lookup"><span data-stu-id="fd642-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="fd642-137">Nesne veri türü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="fd642-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="fd642-138">Bir başvuru türü veya değer türü bir değişkene atayabilirsiniz `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="fd642-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="fd642-139">Bir `Object` değişken her zaman bir başvuru veri hiçbir zaman kendisi tutar.</span><span class="sxs-lookup"><span data-stu-id="fd642-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="fd642-140">Ancak, bir değer türüne atarsanız bir `Object` kendi verilerini tutan gibi değişken davranır.</span><span class="sxs-lookup"><span data-stu-id="fd642-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="fd642-141">Daha fazla bilgi için [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="fd642-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="fd642-142">Olup bulabilirsiniz bir `Object` değişkeni hareket bir başvuru türü veya değer türü olarak geçirerek <xref:Microsoft.VisualBasic.Information.IsReference%2A> yönteminde <xref:Microsoft.VisualBasic.Information> sınıfının <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fd642-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fd642-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> döndürür `True` durumunda içeriğinin `Object` değişkeninin bir başvuru türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd642-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd642-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd642-144">See also</span></span>

- [<span data-ttu-id="fd642-145">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="fd642-146">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="fd642-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="fd642-147">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd642-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="fd642-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fd642-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="fd642-149">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fd642-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="fd642-150">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="fd642-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
