---
description: 'Daha fazla bilgi edinin: dizi dönüştürmeleri (Visual Basic)'
title: Dizi Dönüştürmeler
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
ms.openlocfilehash: 1600042e1d41cbc2bd52468544db0e806e776d9c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466412"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="e04fc-103">Dizi Dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e04fc-103">Array Conversions (Visual Basic)</span></span>

<span data-ttu-id="e04fc-104">Aşağıdaki koşulları karşılamanız kaydıyla, bir dizi türünü farklı bir dizi türüne dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e04fc-104">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="e04fc-105">**Eşit derece.**</span><span class="sxs-lookup"><span data-stu-id="e04fc-105">**Equal Rank.**</span></span> <span data-ttu-id="e04fc-106">İki dizinin dereceleri aynı olmalıdır, diğer bir deyişle, aynı sayıda boyutlara sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="e04fc-106">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="e04fc-107">Ancak, ilgili boyutların uzunluklarının aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e04fc-107">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="e04fc-108">**Öğe veri türü.**</span><span class="sxs-lookup"><span data-stu-id="e04fc-108">**Element Data Type.**</span></span> <span data-ttu-id="e04fc-109">Her iki dizinin öğelerinin veri türleri başvuru türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e04fc-109">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="e04fc-110">`Integer` `Long` `Object` En az bir değer türü dahil olduğu için bir diziyi diziye veya hatta bir diziye dönüştüremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e04fc-110">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="e04fc-111">Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e04fc-111">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="e04fc-112">**Söylebilirlik.**</span><span class="sxs-lookup"><span data-stu-id="e04fc-112">**Convertibility.**</span></span> <span data-ttu-id="e04fc-113">İki dizinin öğe türleri arasında genişletme veya daraltma bir dönüştürme yapılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e04fc-113">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="e04fc-114">Bu gereksinimi başarısız yapan bir örnek, bir `String` dizi ve öğesinden türetilen bir sınıfın dizisi arasında dönüştürme girişiminde bulunur <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e04fc-114">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e04fc-115">Bu iki tür hiçbir şey ortak değildir ve aralarında herhangi bir tür dönüştürme yoktur.</span><span class="sxs-lookup"><span data-stu-id="e04fc-115">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="e04fc-116">Bir dizi türünün diğerine dönüştürülmesi, ilgili öğelerin dönüştürülmesine genişleyen veya daraltma olmasına bağlı olarak genişletme veya daraltma.</span><span class="sxs-lookup"><span data-stu-id="e04fc-116">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="e04fc-117">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e04fc-117">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="e04fc-118">Bir nesne dizisine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e04fc-118">Conversion to an Object Array</span></span>  

 <span data-ttu-id="e04fc-119">Bir diziyi başlatmadan bildirdiğinizde `Object` , öğe türü `Object` başlatılmamış kaldığı sürece.</span><span class="sxs-lookup"><span data-stu-id="e04fc-119">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="e04fc-120">Belirli bir sınıfın dizisine ayarladığınızda, bu sınıfın türünü alır.</span><span class="sxs-lookup"><span data-stu-id="e04fc-120">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="e04fc-121">Ancak, temel alınan türü hala olur `Object` ve daha sonra ilişkisiz bir sınıfın başka bir dizisine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e04fc-121">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="e04fc-122">Tüm sınıflar öğesinden türetildiğinden `Object` , dizinin öğe türünü herhangi bir sınıftan başka bir sınıfa dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e04fc-122">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="e04fc-123">Aşağıdaki örnekte, türler arasında dönüştürme yoktur `student` `String` , ancak her ikisi de öğesinden türetilir, bu `Object` nedenle tüm atamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e04fc-123">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="e04fc-124">Bir dizinin temel alınan türü</span><span class="sxs-lookup"><span data-stu-id="e04fc-124">Underlying Type of an Array</span></span>  

 <span data-ttu-id="e04fc-125">Özgün olarak belirli bir sınıf içeren bir diziyi bildirirseniz, temel alınan öğe türü bu sınıftır.</span><span class="sxs-lookup"><span data-stu-id="e04fc-125">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="e04fc-126">Daha sonra başka bir sınıfın dizisine ayarlarsanız, iki sınıf arasında bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e04fc-126">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="e04fc-127">Aşağıdaki örnekte `students` bir `student` dizidir.</span><span class="sxs-lookup"><span data-stu-id="e04fc-127">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="e04fc-128">Ve arasında dönüştürme olmadığından `String` `student` , son ifade başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e04fc-128">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="e04fc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e04fc-129">See also</span></span>

- [<span data-ttu-id="e04fc-130">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="e04fc-130">Data Types</span></span>](index.md)
- [<span data-ttu-id="e04fc-131">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="e04fc-131">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="e04fc-132">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="e04fc-132">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e04fc-133">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="e04fc-133">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="e04fc-134">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e04fc-134">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="e04fc-135">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="e04fc-135">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="e04fc-136">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e04fc-136">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="e04fc-137">Diziler</span><span class="sxs-lookup"><span data-stu-id="e04fc-137">Arrays</span></span>](../arrays/index.md)
