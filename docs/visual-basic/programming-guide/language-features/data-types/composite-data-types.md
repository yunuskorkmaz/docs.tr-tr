---
title: Bileşik Veri Türleri (Visual Basic)
ms.date: 04/25/2017
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
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833821"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="ccb92-102">Bileşik Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccb92-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="ccb92-103">Başlangıç veri türleri Visual Basic kaynakları'na ek olarak, öğeleri oluşturmak için farklı türde de toplayabilir *bileşik veri türleri* yapılar, diziler ve sınıflar gibi.</span><span class="sxs-lookup"><span data-stu-id="ccb92-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="ccb92-104">Bileşik veri türleri, temel türleri ve diğer bileşik türler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccb92-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="ccb92-105">Örneğin, yapı öğeleri bir dizi veya bir yapı dizi üyeleri ile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccb92-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="ccb92-106">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-106">Data Types</span></span>  
 <span data-ttu-id="ccb92-107">Bileşik tür bileşenlerinden birinin veri türünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb92-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="ccb92-108">Örneğin, bir dizi `Integer` öğeleri değil `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="ccb92-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="ccb92-109">Öğe türü, parantez ve virgül gerektiği gibi kullanarak bir dizi veri türü normal olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="ccb92-110">Örneğin, tek boyutlu bir dizi `String` öğeler olarak temsil edilir `String()`ve iki boyutlu bir dizi `Boolean` öğeler olarak temsil edilir `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="ccb92-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="ccb92-111">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-111">Structure Types</span></span>  
 <span data-ttu-id="ccb92-112">Tüm yapıları kapsayan tek bir veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccb92-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="ccb92-113">Bunun yerine, iki yapıları aynı sırada aynı öğeleri tanımlamak olsa bile her bir yapı tanımının bir benzersiz veri türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ccb92-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="ccb92-114">Ancak, iki veya daha fazla örneğinin aynı yapısını oluşturursanız, Visual Basic bunları aynı veri türünde olmasını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="ccb92-115">Demetler</span><span class="sxs-lookup"><span data-stu-id="ccb92-115">Tuples</span></span>

<span data-ttu-id="ccb92-116">Bir demet eşleşen türleri önceden tanımlanmıştır iki veya daha fazla alan içeren basit bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="ccb92-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="ccb92-117">Diziler, Visual Basic 2017'den itibaren desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="ccb92-118">Diziler başvuruya göre bağımsız değişkenler geçirmek zorunda ya da daha ağır sınıf veya yapı döndürülen alanları paketleme olmadan tek bir yöntem çağrısından birden çok değer döndürmek için en yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccb92-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="ccb92-119">Bkz: [diziler](tuples.md) konu başlıkları hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="ccb92-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="ccb92-120">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-120">Array Types</span></span>  
 <span data-ttu-id="ccb92-121">Tüm diziler kapsayan tek bir veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccb92-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="ccb92-122">Veri türü bir dizi belirli bir örneğini aşağıdaki tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="ccb92-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="ccb92-123">Bir dizi olma olgusu</span><span class="sxs-lookup"><span data-stu-id="ccb92-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="ccb92-124">Dizinin boyut (boyut sayısı)</span><span class="sxs-lookup"><span data-stu-id="ccb92-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="ccb92-125">Dizinin öğe türü</span><span class="sxs-lookup"><span data-stu-id="ccb92-125">The element type of the array</span></span>  
  
 <span data-ttu-id="ccb92-126">Özellikle, belirli bir boyutun uzunluğu örneğinin veri türünün bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="ccb92-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="ccb92-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="ccb92-128">Önceki örnekte, dizi değişkenleri `arrayA` ve `arrayB` aynı veri türü olarak değerlendirilir: `Byte()` — olsa da bunlar için farklı uzunluktaki başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ccb92-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="ccb92-129">Değişkenleri `arrayB` ve `arrayC` kendi öğe türleri farklı olduğundan, aynı türde değildir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="ccb92-130">Değişkenleri `arrayC` ve `arrayD` kendi sıralamalara sahip farklı olduğundan, aynı türde değildir.</span><span class="sxs-lookup"><span data-stu-id="ccb92-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="ccb92-131">Değişkenleri `arrayD` ve `arrayE` aynı türe sahip — `Short(,)` — kendi sıralamalara sahip ve öğe türleri aynı olsa bile olduğundan `arrayD` henüz başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="ccb92-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="ccb92-132">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="ccb92-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="ccb92-133">Sınıf Türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-133">Class Types</span></span>  
 <span data-ttu-id="ccb92-134">Tüm sınıflar kapsayan tek bir veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccb92-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="ccb92-135">Bir sınıf başka bir sınıftan devralabilir olsa da, her bir ayrı veri türü olan.</span><span class="sxs-lookup"><span data-stu-id="ccb92-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="ccb92-136">Aynı sınıfın birden çok örneği aynı veri türü var.</span><span class="sxs-lookup"><span data-stu-id="ccb92-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="ccb92-137">Başka bir sınıf örneği değişkenini atarsanız, yalnızca aynı veri türüne sahip değilsiniz, bellekte aynı sınıf örneğine işaret edecek.</span><span class="sxs-lookup"><span data-stu-id="ccb92-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="ccb92-138">Sınıflar hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ccb92-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb92-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccb92-139">See also</span></span>

- [<span data-ttu-id="ccb92-140">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="ccb92-141">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="ccb92-142">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="ccb92-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="ccb92-143">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="ccb92-144">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="ccb92-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="ccb92-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="ccb92-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ccb92-146">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="ccb92-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="ccb92-147">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma</span><span class="sxs-lookup"><span data-stu-id="ccb92-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
