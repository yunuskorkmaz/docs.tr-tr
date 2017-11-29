---
title: "Dizi Dönüştürmeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="c1ba7-102">Dizi Dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1ba7-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="c1ba7-103">Aşağıdaki koşullara uyması şartıyla farklı dizi türü için bir dizi türü dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c1ba7-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="c1ba7-104">**Eşit derece.**</span><span class="sxs-lookup"><span data-stu-id="c1ba7-104">**Equal Rank.**</span></span> <span data-ttu-id="c1ba7-105">İki dizi sıralar aynı olması gerekir, diğer bir deyişle, Boyutlar aynı sayıda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="c1ba7-106">Ancak, uzunlukları ilgili boyutlarının aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="c1ba7-107">**Öğe veri türü.**</span><span class="sxs-lookup"><span data-stu-id="c1ba7-107">**Element Data Type.**</span></span> <span data-ttu-id="c1ba7-108">Veri türleri iki dizi öğelerinin başvuru türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="c1ba7-109">Dönüştüremezsiniz bir `Integer` için dizi bir `Long` dizi veya hatta için bir `Object` en az bir değer türü olduğundan, dizi.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="c1ba7-110">Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c1ba7-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="c1ba7-111">**Convertibility.**</span><span class="sxs-lookup"><span data-stu-id="c1ba7-111">**Convertibility.**</span></span> <span data-ttu-id="c1ba7-112">Genişletme veya daraltma, dönüştürme, iki dizi öğesi türleri arasında mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="c1ba7-113">Bu gereksinim başarısız arasında denenen bir dönüştürme örneğidir bir `String` dizi ve bir sınıf bir dizi türetilen <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c1ba7-114">Bu iki tür ortak ilgisi yoktur ve bunlar arasında herhangi bir türde bir dönüştürme yok vardır.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="c1ba7-115">Bir dizi türü bir dönüştürme başka bir genişletme veya daraltma olup ilgili öğeleri dönüştürülmesi genişletme daraltma veya bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="c1ba7-116">Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c1ba7-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="c1ba7-117">Bir nesne dizisine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c1ba7-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="c1ba7-118">Ne zaman bildirdiğiniz bir `Object` , alt öğe türü başlatma olmadan dizisi `Object` başlatılmamış kaldığı sürece.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="c1ba7-119">Belirli bir sınıfın bir diziye ayarladığınızda, o sınıfın türü alır.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="c1ba7-120">Ancak, temel alınan türü hala olduğunu `Object`, ve daha sonra ilişkisiz bir sınıfın başka diziye ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="c1ba7-121">Tüm sınıflar türetmek beri `Object`, başka bir sınıf herhangi bir sınıfın dizinin öğesi türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="c1ba7-122">Aşağıdaki örnekte, türleri arasında dönüştürme var `student` ve `String`, ancak her ikisi de öğesinden türetilen `Object`, tüm atamaları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="c1ba7-123">Bir dizi temel alınan türü</span><span class="sxs-lookup"><span data-stu-id="c1ba7-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="c1ba7-124">İlk olarak bir dizi belirli bir sınıf ile bildirirseniz, temel alınan öğe türü bu sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="c1ba7-125">Daha sonra başka bir sınıfın bir diziye ayarlarsanız, iki sınıf arasında dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="c1ba7-126">Aşağıdaki örnekte, `students` olan bir `student` dizi.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="c1ba7-127">Arasında dönüştürme mevcut olduğundan `String` ve `student`, son deyim başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1ba7-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ba7-128">See Also</span></span>  
 [<span data-ttu-id="c1ba7-129">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c1ba7-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="c1ba7-130">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="c1ba7-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="c1ba7-131">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c1ba7-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="c1ba7-132">Dizeler ve diğer türleri arasında dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c1ba7-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="c1ba7-133">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="c1ba7-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="c1ba7-134">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c1ba7-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="c1ba7-135">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="c1ba7-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c1ba7-136">Diziler</span><span class="sxs-lookup"><span data-stu-id="c1ba7-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
