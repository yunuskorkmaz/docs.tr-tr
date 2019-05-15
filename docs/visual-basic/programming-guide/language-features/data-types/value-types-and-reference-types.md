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
ms.openlocfilehash: 541fe9f176a6210372b58753254692142f086992
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589826"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="7304a-102">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-102">Value Types and Reference Types</span></span>
<span data-ttu-id="7304a-103">Visual Basic'de Veri türleri sınıflandırmalarına göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7304a-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="7304a-104">Visual Basic veri türleri, belirli bir tür değişkeninin kendi verilerini veya verileri için bir işaretçi depolar göre sınıflandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7304a-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="7304a-105">Kendi verilerini depolayan ise bir *değer türü*; başka bir yerde olduğu bellekteki verileri için bir işaretçi tutan bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="7304a-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="7304a-106">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-106">Value Types</span></span>  
 <span data-ttu-id="7304a-107">Bir veri türü olan bir *değer türü* kendi bellek ayırma verileri tutuyorsa.</span><span class="sxs-lookup"><span data-stu-id="7304a-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="7304a-108">Değer türleri aşağıdakileri kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="7304a-108">Value types include the following:</span></span>  
  
- <span data-ttu-id="7304a-109">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-109">All numeric data types</span></span>  
  
- <span data-ttu-id="7304a-110">`Boolean`, `Char`, ve `Date`</span><span class="sxs-lookup"><span data-stu-id="7304a-110">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="7304a-111">Başvuru türleri üyelerinin olması durumunda bile tüm yapıları</span><span class="sxs-lookup"><span data-stu-id="7304a-111">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="7304a-112">Her zaman kendi temel türü olduğundan numaralandırmalar `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, veya `ULong`</span><span class="sxs-lookup"><span data-stu-id="7304a-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="7304a-113">Başvuru türü üyeleri içeren olsa bile her bir değer türü yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="7304a-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="7304a-114">Bu nedenle, değer türleri gibi `Char` ve `Integer` .NET Framework yapıları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7304a-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="7304a-115">Ayrılmış anahtar sözcüğü, örneğin,'ı kullanarak bir değer türü bildirebilirsiniz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="7304a-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="7304a-116">Ayrıca `New` anahtar sözcüğü, bir değer türü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="7304a-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="7304a-117">Tür parametreleri alan bir oluşturucu sahipse, bu özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7304a-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="7304a-118">Bunun bir örneği <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> yeni bir derleme Oluşturucu `Decimal` sağlanan parçalarından değeri.</span><span class="sxs-lookup"><span data-stu-id="7304a-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="7304a-119">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-119">Reference Types</span></span>  
 <span data-ttu-id="7304a-120">A *başvuru türüne* verilerini tutan başka bir bellek konumuna bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="7304a-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="7304a-121">Başvuru türleri aşağıdakileri kapsamaktadır:</span><span class="sxs-lookup"><span data-stu-id="7304a-121">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="7304a-122">Tüm diziler, kendi öğeleri değer türleri olsa bile</span><span class="sxs-lookup"><span data-stu-id="7304a-122">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="7304a-123">Sınıfı, gibi türleri <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="7304a-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="7304a-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="7304a-124">Delegates</span></span>  
  
 <span data-ttu-id="7304a-125">Bir sınıf bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="7304a-125">A class is a *reference type*.</span></span> <span data-ttu-id="7304a-126">Bu nedenle, başvuru türleri gibi `Object` ve `String` .NET Framework sınıfları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7304a-126">For this reason, reference types such as `Object` and `String` are supported by .NET Framework classes.</span></span> <span data-ttu-id="7304a-127">Üyeleri, değer türleri olsa bile, her dizide bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7304a-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="7304a-128">Her bir başvuru türü temel alınan bir .NET Framework sınıfı temsil eder. bu yana kullanmalısınız [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) başlattığınızda, anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7304a-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="7304a-129">Aşağıdaki deyim, bir dizi başlatır.</span><span class="sxs-lookup"><span data-stu-id="7304a-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="7304a-130">Türleri öğeleri</span><span class="sxs-lookup"><span data-stu-id="7304a-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="7304a-131">Bunların hiçbirine olarak bildirilen bir öğe için bir veri türü belirtilemez çünkü aşağıdaki programlama öğeleri türleri olarak nitelendirmeyin:</span><span class="sxs-lookup"><span data-stu-id="7304a-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="7304a-132">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="7304a-132">Namespaces</span></span>  
  
- <span data-ttu-id="7304a-133">Modüller</span><span class="sxs-lookup"><span data-stu-id="7304a-133">Modules</span></span>  
  
- <span data-ttu-id="7304a-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="7304a-134">Events</span></span>  
  
- <span data-ttu-id="7304a-135">Özellikler ve yordamlar</span><span class="sxs-lookup"><span data-stu-id="7304a-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="7304a-136">Değişkenleri, sabitleri ve alanlar</span><span class="sxs-lookup"><span data-stu-id="7304a-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="7304a-137">Nesne veri türü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="7304a-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="7304a-138">Bir başvuru türü veya değer türü bir değişkene atayabilirsiniz `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="7304a-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="7304a-139">Bir `Object` değişken veri için hiçbir zaman kendisi her zaman bir işaretçi tutar.</span><span class="sxs-lookup"><span data-stu-id="7304a-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="7304a-140">Ancak, bir değer türüne atarsanız bir `Object` kendi verilerini tutan gibi değişken davranır.</span><span class="sxs-lookup"><span data-stu-id="7304a-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="7304a-141">Daha fazla bilgi için [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7304a-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="7304a-142">Olup bulabilirsiniz bir `Object` değişkeni hareket bir başvuru türü veya değer türü olarak geçirerek <xref:Microsoft.VisualBasic.Information.IsReference%2A> yönteminde <xref:Microsoft.VisualBasic.Information> sınıfının <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7304a-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="7304a-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> döndürür `True` durumunda içeriğinin `Object` değişkeninin bir başvuru türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7304a-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7304a-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7304a-144">See also</span></span>

- [<span data-ttu-id="7304a-145">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7304a-146">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="7304a-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="7304a-147">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="7304a-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="7304a-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="7304a-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="7304a-149">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7304a-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="7304a-150">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="7304a-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
