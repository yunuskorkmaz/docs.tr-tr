---
title: Dizi Dönüştürmeleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 93e6365a70f52f730b016cd4d4ac9382baeeba55
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784887"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="f6a5d-102">Dizi Dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6a5d-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="f6a5d-103">Aşağıdaki koşulları karşılaması koşuluyla, bir dizi türü farklı bir dizi türüne dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f6a5d-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="f6a5d-104">**Eşit boyut.**</span><span class="sxs-lookup"><span data-stu-id="f6a5d-104">**Equal Rank.**</span></span> <span data-ttu-id="f6a5d-105">Sıralamalara sahip iki dizinin aynı olmalıdır, yani boyut sayıları aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="f6a5d-106">Ancak, ilgili boyutların uzunlukları aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="f6a5d-107">**Öğe veri türü.**</span><span class="sxs-lookup"><span data-stu-id="f6a5d-107">**Element Data Type.**</span></span> <span data-ttu-id="f6a5d-108">İki dizi öğeleri veri türleri, başvuru türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="f6a5d-109">Dönüştüremezsiniz bir `Integer` için dizi bir `Long` dizisi geçirin veya hatta için bir `Object` dizisi en az bir değer türü olduğundan.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="f6a5d-110">Daha fazla bilgi için [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="f6a5d-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="f6a5d-111">**Convertibility.**</span><span class="sxs-lookup"><span data-stu-id="f6a5d-111">**Convertibility.**</span></span> <span data-ttu-id="f6a5d-112">Genişletme veya daraltma, dönüştürme, olası iki dizi öğesi türleri arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="f6a5d-113">Bu gereksinim başarısız bir örnek denenen bir dönüştürme arasında olan bir `String` dizi ve bir sınıf bir dizi türetilen <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f6a5d-114">Ortak hiçbir şey bu iki tür vardır ve bunlar arasında dönüştürme herhangi bir türde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="f6a5d-115">Bir dizi türünde bir dönüştürme diğerine genişletme veya ilgili öğelerin dönüştürme genişletme daraltma mı bağlı olarak daraltma.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="f6a5d-116">Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f6a5d-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="f6a5d-117">Bir nesne dizisine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f6a5d-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="f6a5d-118">Bildirdiğinizde bir `Object` dizisi bu öğe türünün başlatma olmadan `Object` başlatılmamış kaldığı sürece.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="f6a5d-119">Belirli bir sınıfın bir diziye ayarladığınızda, bu sınıf türüne göre alır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="f6a5d-120">Ancak, temel alınan türü hala geçerli olduğunu `Object`, ve ardından ilişkisiz bir sınıfın başka bir dizi için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="f6a5d-121">Tüm sınıflar türetilen beri `Object`, dizinin öğe türü herhangi bir sınıfın herhangi bir sınıf için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="f6a5d-122">Aşağıdaki örnekte, türleri arasında dönüştürme var `student` ve `String`, ancak her ikisini de öğesinden türetilen `Object`, tüm atamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="f6a5d-123">Bir dizi temel alınan türü</span><span class="sxs-lookup"><span data-stu-id="f6a5d-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="f6a5d-124">İlk olarak belirli bir sınıfı olan bir dizi bildirirseniz, temel alınan öğe türünün bu sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="f6a5d-125">Daha sonra başka bir sınıfın bir diziye ayarlarsanız, iki sınıf arasında bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="f6a5d-126">Aşağıdaki örnekte, `students` olduğu bir `student` dizi.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="f6a5d-127">Arasında dönüştürme mevcut olduğundan `String` ve `student`, son deyim başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6a5d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6a5d-128">See Also</span></span>  
 [<span data-ttu-id="f6a5d-129">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f6a5d-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="f6a5d-130">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="f6a5d-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="f6a5d-131">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f6a5d-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="f6a5d-132">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f6a5d-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="f6a5d-133">Nasıl yapılır: bir nesneyi Visual Basic'de başka bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f6a5d-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="f6a5d-134">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f6a5d-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="f6a5d-135">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f6a5d-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="f6a5d-136">Diziler</span><span class="sxs-lookup"><span data-stu-id="f6a5d-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
