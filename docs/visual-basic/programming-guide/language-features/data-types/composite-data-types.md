---
title: Bileşik Veri Türleri
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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394304"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="8cd27-102">Bileşik Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cd27-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="8cd27-103">Visual Basic tedariklerini temel veri türlerine ek olarak, yapılar, diziler ve sınıflar gibi *bileşik veri türleri* oluşturmak için farklı türlerdeki öğeleri de birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cd27-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="8cd27-104">Birleşik veri türlerini temel türler ve diğer bileşik türlerden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cd27-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="8cd27-105">Örneğin, bir yapı öğeleri dizisi veya dizi üyeleri olan bir yapı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8cd27-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="8cd27-106">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-106">Data Types</span></span>  
 <span data-ttu-id="8cd27-107">Bileşik tür, bileşenlerinden herhangi birinin veri türünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8cd27-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="8cd27-108">Örneğin, bir dizi `Integer` öğe `Integer` veri türünde değil.</span><span class="sxs-lookup"><span data-stu-id="8cd27-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="8cd27-109">Dizi veri türü, normalde öğe türü, parantezler ve gereken virgüller kullanılarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="8cd27-110">Örneğin, tek boyutlu bir `String` öğe dizisi olarak temsil edilir `String()` ve iki boyutlu bir `Boolean` öğe dizisi olarak temsil edilir `Boolean(,)` .</span><span class="sxs-lookup"><span data-stu-id="8cd27-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="8cd27-111">Yapı türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-111">Structure Types</span></span>  
 <span data-ttu-id="8cd27-112">Tüm yapıları kapsayan tek bir veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="8cd27-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="8cd27-113">Bunun yerine, bir yapının her tanımı, iki yapı aynı sırada aynı öğeleri tanımlasa bile benzersiz bir veri türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8cd27-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="8cd27-114">Ancak, aynı yapının iki veya daha fazla örneğini oluşturursanız Visual Basic, bunları aynı veri türünde olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="8cd27-115">Demetler</span><span class="sxs-lookup"><span data-stu-id="8cd27-115">Tuples</span></span>

<span data-ttu-id="8cd27-116">Kayıt düzeni, türleri önceden tanımlanmış iki veya daha fazla alan içeren hafif bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="8cd27-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="8cd27-117">Tanımlama grupları Visual Basic 2017 ' den başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="8cd27-118">Tanımlama alanları, bağımsız değişkenleri başvuruya göre geçirmek veya döndürülen alanları daha ağır bir sınıfta veya yapıda paketlemek zorunda kalmadan, tek bir yöntem çağrısından birden çok değer döndürmek için en yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8cd27-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="8cd27-119">Tanımlama grupları hakkında daha fazla bilgi için [Tanımlama grupları](tuples.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8cd27-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="8cd27-120">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-120">Array Types</span></span>  
 <span data-ttu-id="8cd27-121">Tüm dizileri kapsayan tek veri türü yok.</span><span class="sxs-lookup"><span data-stu-id="8cd27-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="8cd27-122">Bir dizinin belirli bir örneğinin veri türü aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="8cd27-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="8cd27-123">Bir dizi olması</span><span class="sxs-lookup"><span data-stu-id="8cd27-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="8cd27-124">Dizinin derecesi (boyut sayısı)</span><span class="sxs-lookup"><span data-stu-id="8cd27-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="8cd27-125">Dizinin öğe türü</span><span class="sxs-lookup"><span data-stu-id="8cd27-125">The element type of the array</span></span>  
  
 <span data-ttu-id="8cd27-126">Özellikle, belirli bir boyutun uzunluğu örneğin veri türünün bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="8cd27-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="8cd27-128">Önceki örnekte, dizi değişkenleri `arrayA` ve `arrayB` aynı veri türünde olduğu kabul edilir — `Byte()` ancak farklı uzunluklara başlatılsalar bile.</span><span class="sxs-lookup"><span data-stu-id="8cd27-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="8cd27-129">Değişkenlerini `arrayB` ve `arrayC` öğe türleri farklı olduğundan aynı türde değil.</span><span class="sxs-lookup"><span data-stu-id="8cd27-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="8cd27-130">`arrayC`Ve `arrayD` dereceleri farklı olduğundan, değişkenler aynı türde değil.</span><span class="sxs-lookup"><span data-stu-id="8cd27-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="8cd27-131">Değişkenleri `arrayD` ve `arrayE` `Short(,)` öğe türleri aynı olmalıdır, ancak henüz başlatılmamış olsa da, kendi dereceleri ve öğe türleri aynı türde `arrayD` .</span><span class="sxs-lookup"><span data-stu-id="8cd27-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="8cd27-132">Diziler hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cd27-132">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="8cd27-133">Sınıf Türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-133">Class Types</span></span>  
 <span data-ttu-id="8cd27-134">Tüm sınıflardan oluşan tek bir veri türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="8cd27-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="8cd27-135">Bir sınıf başka bir sınıftan devralınabilir olsa da, her biri ayrı bir veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="8cd27-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="8cd27-136">Aynı sınıfın birden çok örneği aynı veri türündedir.</span><span class="sxs-lookup"><span data-stu-id="8cd27-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="8cd27-137">Bir sınıf örneği değişkenini diğerine atarsanız, yalnızca aynı veri türüne sahip olmaları gerekmez, bellekte aynı sınıf örneğine işaret ederler.</span><span class="sxs-lookup"><span data-stu-id="8cd27-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="8cd27-138">Sınıflar hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="8cd27-138">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd27-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cd27-139">See also</span></span>

- [<span data-ttu-id="8cd27-140">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="8cd27-141">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-141">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="8cd27-142">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="8cd27-142">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="8cd27-143">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-143">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="8cd27-144">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8cd27-144">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="8cd27-145">Yapılar</span><span class="sxs-lookup"><span data-stu-id="8cd27-145">Structures</span></span>](structures.md)
- [<span data-ttu-id="8cd27-146">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8cd27-146">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="8cd27-147">Nasıl yapılır: Değişkende Birden Fazla Değer Tutma</span><span class="sxs-lookup"><span data-stu-id="8cd27-147">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
