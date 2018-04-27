---
title: Değer Türleri ve Başvuru Türleri
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cbab25e4af6b96ae22fe18d0b8a8fdbc7a7c7a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="cdfbe-102">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-102">Value Types and Reference Types</span></span>
<span data-ttu-id="cdfbe-103">Visual Basic veri türleri sınıflandırmalarına göre uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="cdfbe-104">Visual Basic veri türleri, belirli türde bir değişken kendi veri veya veri için bir işaretçi depolar göre sınıflandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="cdfbe-105">Kendi verilerini depolayan ise bir *değer türü*; başka bir yerde bu bellek verileri için bir işaretçi barındırıyorsa bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="cdfbe-106">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-106">Value Types</span></span>  
 <span data-ttu-id="cdfbe-107">Bir veri türü olan bir *değer türü* kendi bellek ayırma içindeki verilere tutuyorsa.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="cdfbe-108">Değer türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cdfbe-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="cdfbe-109">Tüm sayısal veri türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="cdfbe-110">`Boolean`, `Char`, ve `Date`</span><span class="sxs-lookup"><span data-stu-id="cdfbe-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="cdfbe-111">Başvuru türleri üyeleri olan olsa bile tüm yapıları</span><span class="sxs-lookup"><span data-stu-id="cdfbe-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="cdfbe-112">Kendi temel alınan türü her zaman olduğundan numaralandırmalar `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, veya `ULong`</span><span class="sxs-lookup"><span data-stu-id="cdfbe-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="cdfbe-113">Başvuru türü üyeleri içerse bile, her bir değer türü yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="cdfbe-114">Bu nedenle, değer türleri gibi `Char` ve `Integer` .NET Framework yapıları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="cdfbe-115">Ayrılmış bir anahtar sözcük, örneğin, kullanarak bir değer türü bildirebilirsiniz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="cdfbe-116">Aynı zamanda `New` anahtar sözcüğü bir değer türü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="cdfbe-117">Bu tür parametreler isteyen bir kurucusunun özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="cdfbe-118">Bunun bir örneği <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> yeni yapılar Oluşturucusu `Decimal` sağlanan bölümlerinden değeri.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="cdfbe-119">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-119">Reference Types</span></span>  
 <span data-ttu-id="cdfbe-120">A *başvuru türüne* verilerini tutan başka bir bellek konumunu gösteren bir işaretçi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="cdfbe-121">Başvuru türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cdfbe-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="cdfbe-122">Değer türleri kendi öğeleridir olsa bile tüm diziler</span><span class="sxs-lookup"><span data-stu-id="cdfbe-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="cdfbe-123">Sınıf türleri, gibi <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="cdfbe-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="cdfbe-124">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="cdfbe-124">Delegates</span></span>  
  
 <span data-ttu-id="cdfbe-125">Bir sınıf bir *başvuru türüne*.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-125">A class is a *reference type*.</span></span> <span data-ttu-id="cdfbe-126">Bu nedenle, başvuru türleri gibi `Object` ve `String` tarafından desteklenen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="cdfbe-127">Değer türleri üyeleri olsa bile, her dizi bir başvuru türü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="cdfbe-128">Her başvuru türündeki temel alınan bir .NET Framework sınıfı temsil ettiği kullanmalısınız [New işleci](../../../../visual-basic/language-reference/operators/new-operator.md) , Initialize when anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="cdfbe-129">Aşağıdaki deyim, bir dizi başlatır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="cdfbe-130">Türleri olmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="cdfbe-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="cdfbe-131">Bildirilen öğe için bir veri türü olarak hiçbirini belirtilemez çünkü aşağıdaki programlama öğeleri türleri olarak nitelemek değil:</span><span class="sxs-lookup"><span data-stu-id="cdfbe-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="cdfbe-132">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="cdfbe-132">Namespaces</span></span>  
  
-   <span data-ttu-id="cdfbe-133">Modüller</span><span class="sxs-lookup"><span data-stu-id="cdfbe-133">Modules</span></span>  
  
-   <span data-ttu-id="cdfbe-134">Olaylar</span><span class="sxs-lookup"><span data-stu-id="cdfbe-134">Events</span></span>  
  
-   <span data-ttu-id="cdfbe-135">Özellikler ve yordamları</span><span class="sxs-lookup"><span data-stu-id="cdfbe-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="cdfbe-136">Değişkenlerinin, sabitleri ve alanlar</span><span class="sxs-lookup"><span data-stu-id="cdfbe-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="cdfbe-137">Nesne veri türü ile çalışma</span><span class="sxs-lookup"><span data-stu-id="cdfbe-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="cdfbe-138">Bir değişken için bir başvuru türü veya bir değer türü atayabilirsiniz `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="cdfbe-139">Bir `Object` değişkeni verileri verilerin kendisini hiçbir zaman, her zaman bir işaretçi tutar.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="cdfbe-140">Ancak, bir değer türü atarsanız bir `Object` kendi verilerini varmış gibi değişken, davranır.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="cdfbe-141">Daha fazla bilgi için bkz: [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="cdfbe-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="cdfbe-142">Tanımlanmadığını bulabileceğiniz bir `Object` değişken işlevi gören bir başvuru türü veya bir değer türü olarak geçirerek <xref:Microsoft.VisualBasic.Information.IsReference%2A> yönteminde <xref:Microsoft.VisualBasic.Information> sınıfının <xref:Microsoft.VisualBasic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="cdfbe-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> döndürür `True` varsa içeriğini `Object` değişkeni bir başvuru türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfbe-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdfbe-144">See Also</span></span>  
 [<span data-ttu-id="cdfbe-145">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="cdfbe-146">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="cdfbe-147">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="cdfbe-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="cdfbe-148">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="cdfbe-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="cdfbe-149">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cdfbe-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="cdfbe-150">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="cdfbe-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
