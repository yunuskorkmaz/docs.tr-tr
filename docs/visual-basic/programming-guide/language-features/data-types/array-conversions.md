---
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
ms.openlocfilehash: 375c75c954f3be535272d674d9b786cad46b1a01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077195"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="d69a8-102">Dizi Dönüştürmeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d69a8-102">Array Conversions (Visual Basic)</span></span>

<span data-ttu-id="d69a8-103">Aşağıdaki koşulları karşılamanız kaydıyla, bir dizi türünü farklı bir dizi türüne dönüştürebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d69a8-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="d69a8-104">**Eşit derece.**</span><span class="sxs-lookup"><span data-stu-id="d69a8-104">**Equal Rank.**</span></span> <span data-ttu-id="d69a8-105">İki dizinin dereceleri aynı olmalıdır, diğer bir deyişle, aynı sayıda boyutlara sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="d69a8-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="d69a8-106">Ancak, ilgili boyutların uzunluklarının aynı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d69a8-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="d69a8-107">**Öğe veri türü.**</span><span class="sxs-lookup"><span data-stu-id="d69a8-107">**Element Data Type.**</span></span> <span data-ttu-id="d69a8-108">Her iki dizinin öğelerinin veri türleri başvuru türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d69a8-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="d69a8-109">`Integer` `Long` `Object` En az bir değer türü dahil olduğu için bir diziyi diziye veya hatta bir diziye dönüştüremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d69a8-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="d69a8-110">Daha fazla bilgi için bkz. [değer türleri ve başvuru türleri](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="d69a8-110">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="d69a8-111">**Söylebilirlik.**</span><span class="sxs-lookup"><span data-stu-id="d69a8-111">**Convertibility.**</span></span> <span data-ttu-id="d69a8-112">İki dizinin öğe türleri arasında genişletme veya daraltma bir dönüştürme yapılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d69a8-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="d69a8-113">Bu gereksinimi başarısız yapan bir örnek, bir `String` dizi ve öğesinden türetilen bir sınıfın dizisi arasında dönüştürme girişiminde bulunur <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d69a8-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d69a8-114">Bu iki tür hiçbir şey ortak değildir ve aralarında herhangi bir tür dönüştürme yoktur.</span><span class="sxs-lookup"><span data-stu-id="d69a8-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="d69a8-115">Bir dizi türünün diğerine dönüştürülmesi, ilgili öğelerin dönüştürülmesine genişleyen veya daraltma olmasına bağlı olarak genişletme veya daraltma.</span><span class="sxs-lookup"><span data-stu-id="d69a8-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="d69a8-116">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d69a8-116">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="d69a8-117">Bir nesne dizisine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d69a8-117">Conversion to an Object Array</span></span>  

 <span data-ttu-id="d69a8-118">Bir diziyi başlatmadan bildirdiğinizde `Object` , öğe türü `Object` başlatılmamış kaldığı sürece.</span><span class="sxs-lookup"><span data-stu-id="d69a8-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="d69a8-119">Belirli bir sınıfın dizisine ayarladığınızda, bu sınıfın türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d69a8-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="d69a8-120">Ancak, temel alınan türü hala olur `Object` ve daha sonra ilişkisiz bir sınıfın başka bir dizisine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d69a8-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="d69a8-121">Tüm sınıflar öğesinden türetildiğinden `Object` , dizinin öğe türünü herhangi bir sınıftan başka bir sınıfa dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d69a8-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="d69a8-122">Aşağıdaki örnekte, türler arasında dönüştürme yoktur `student` `String` , ancak her ikisi de öğesinden türetilir, bu `Object` nedenle tüm atamalar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d69a8-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="d69a8-123">Bir dizinin temel alınan türü</span><span class="sxs-lookup"><span data-stu-id="d69a8-123">Underlying Type of an Array</span></span>  

 <span data-ttu-id="d69a8-124">Özgün olarak belirli bir sınıf içeren bir diziyi bildirirseniz, temel alınan öğe türü bu sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d69a8-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="d69a8-125">Daha sonra başka bir sınıfın dizisine ayarlarsanız, iki sınıf arasında bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d69a8-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="d69a8-126">Aşağıdaki örnekte `students` bir `student` dizidir.</span><span class="sxs-lookup"><span data-stu-id="d69a8-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="d69a8-127">Ve arasında dönüştürme olmadığından `String` `student` , son ifade başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d69a8-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="d69a8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d69a8-128">See also</span></span>

- [<span data-ttu-id="d69a8-129">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d69a8-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="d69a8-130">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="d69a8-130">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="d69a8-131">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d69a8-131">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d69a8-132">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="d69a8-132">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="d69a8-133">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d69a8-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="d69a8-134">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d69a8-134">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="d69a8-135">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d69a8-135">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d69a8-136">Diziler</span><span class="sxs-lookup"><span data-stu-id="d69a8-136">Arrays</span></span>](../arrays/index.md)
