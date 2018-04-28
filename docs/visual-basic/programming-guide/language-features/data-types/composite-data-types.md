---
title: Bileşik Veri Türleri (Visual Basic)
ms.custom: ''
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: caa832fc191ad925674e21b1237ac98328ce0bd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="292e6-102">Bileşik Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="292e6-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="292e6-103">Başlangıç veri türleri Visual Basic kaynakları ek olarak, öğeleri oluşturmak için farklı türlerde de toplayabilir *bileşik veri türleri* yapıları, dizileri ve sınıflar gibi.</span><span class="sxs-lookup"><span data-stu-id="292e6-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="292e6-104">Bileşik veri türleri başlangıç türleri ve diğer bileşik türler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292e6-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="292e6-105">Örneğin, dizi üyeleriyle yapı öğeleri dizisi veya bir yapı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="292e6-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="292e6-106">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-106">Data Types</span></span>  
 <span data-ttu-id="292e6-107">Bileşik tür bileşenlerinin hiçbiri veri türünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="292e6-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="292e6-108">Örneğin, bir dizi `Integer` öğeleri değil `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="292e6-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="292e6-109">Öğe türü, parantez ve virgül gerektiği gibi kullanarak bir dizi veri türü normal olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="292e6-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="292e6-110">Örneğin, tek boyutlu dizi `String` öğeler olarak temsil edilir `String()`ve iki boyutlu bir dizi `Boolean` öğeler olarak temsil edilir `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="292e6-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="292e6-111">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-111">Structure Types</span></span>  
 <span data-ttu-id="292e6-112">Tüm yapıları kapsayan tek bir veri türü yok.</span><span class="sxs-lookup"><span data-stu-id="292e6-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="292e6-113">Bunun yerine, iki yapıları aynı sırada aynı öğeleri tanımlamak olsa bile her bir yapı tanımının bir benzersiz veri türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="292e6-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="292e6-114">Ancak, aynı yapısı iki veya daha fazla örneğinin oluşturursanız, Visual Basic bunları aynı veri türünde olmasını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="292e6-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="292e6-115">Demetler</span><span class="sxs-lookup"><span data-stu-id="292e6-115">Tuples</span></span>

<span data-ttu-id="292e6-116">Bir tanımlama grubu, türleri önceden tanımlanmış iki veya daha fazla alan içeren basit bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="292e6-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="292e6-117">Diziler, Visual Basic 2017 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="292e6-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="292e6-118">Diziler, en yaygın olarak başvuruya göre bağımsız değişkenler geçirmek zorunda ya da daha ağır sınıf veya yapı döndürülen alanları paketleme olmadan bir tek bir yöntem çağrısında birden çok değer döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="292e6-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="292e6-119">Bkz: [diziler](tuples.md) konu başlıkları hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="292e6-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="292e6-120">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-120">Array Types</span></span>  
 <span data-ttu-id="292e6-121">Tüm diziler kapsayan tek bir veri türü yok.</span><span class="sxs-lookup"><span data-stu-id="292e6-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="292e6-122">Veri türü bir dizi belirli bir örneği aşağıdaki tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="292e6-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="292e6-123">Bir dizi olma olgusu</span><span class="sxs-lookup"><span data-stu-id="292e6-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="292e6-124">Dizi derecesini (dimensions sayısı)</span><span class="sxs-lookup"><span data-stu-id="292e6-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="292e6-125">Dizi öğesi türü</span><span class="sxs-lookup"><span data-stu-id="292e6-125">The element type of the array</span></span>  
  
 <span data-ttu-id="292e6-126">Özellikle, belirli bir boyut uzunluğu Örneğin veri türü bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="292e6-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="292e6-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="292e6-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="292e6-128">Önceki örnekte değişkenleri dizi `arrayA` ve `arrayB` aynı veri türünde olduğu kabul edilir — `Byte()` — rağmen farklı uzunlukta başlatılır.</span><span class="sxs-lookup"><span data-stu-id="292e6-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="292e6-129">Değişkenleri `arrayB` ve `arrayC` öğesi türlerini farklı olduğu için aynı türde değildir.</span><span class="sxs-lookup"><span data-stu-id="292e6-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="292e6-130">Değişkenleri `arrayC` ve `arrayD` kendi sıralar farklı olduğu için aynı türde değildir.</span><span class="sxs-lookup"><span data-stu-id="292e6-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="292e6-131">Değişkenleri `arrayD` ve `arrayE` aynı türe sahip — `Short(,)` —, sıralar ve öğe türleri aynı rağmen olduğundan `arrayD` henüz başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="292e6-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="292e6-132">Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="292e6-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="292e6-133">Sınıf Türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-133">Class Types</span></span>  
 <span data-ttu-id="292e6-134">Tüm sınıflar kapsayan tek bir veri türü yok.</span><span class="sxs-lookup"><span data-stu-id="292e6-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="292e6-135">Bir sınıf başka bir sınıfı devralabilirsiniz rağmen her bir ayrı veri türü içerir.</span><span class="sxs-lookup"><span data-stu-id="292e6-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="292e6-136">Aynı sınıfın birden çok örneği aynı veri türünde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="292e6-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="292e6-137">Başka bir sınıf örneği değişkeni atarsanız, yalnızca aynı veri türüne sahip değillerse, aynı sınıf örneği bellekte fareyle.</span><span class="sxs-lookup"><span data-stu-id="292e6-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="292e6-138">Sınıfları hakkında daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="292e6-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292e6-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="292e6-139">See Also</span></span>  
 [<span data-ttu-id="292e6-140">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="292e6-141">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="292e6-142">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="292e6-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="292e6-143">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="292e6-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="292e6-144">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="292e6-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="292e6-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="292e6-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="292e6-146">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="292e6-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="292e6-147">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma</span><span class="sxs-lookup"><span data-stu-id="292e6-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
