---
title: Nesne Değişkeni Değerleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: c17c5f85952596f0a080ca473e8f792740e66b8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054191"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="c1055-102">Nesne Değişkeni Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1055-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="c1055-103">Bir değişken [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) herhangi bir türde veri başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c1055-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="c1055-104">Değerin, depolamanın bir `Object` değişkeni tutulur başka bir yerde bellekte değişken bir işaretçi verileri tutan sırada.</span><span class="sxs-lookup"><span data-stu-id="c1055-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="c1055-105">Nesne sınıflandırıcı işlevleri</span><span class="sxs-lookup"><span data-stu-id="c1055-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="c1055-106">Visual Basic hakkında bilgi döndüren işlevleri sağlayan bir `Object` değişken için aşağıdaki tabloda gösterildiği gibi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c1055-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="c1055-107">İşlev</span><span class="sxs-lookup"><span data-stu-id="c1055-107">Function</span></span>|<span data-ttu-id="c1055-108">Nesne değişkeni başvuruyorsa, True döndürür</span><span class="sxs-lookup"><span data-stu-id="c1055-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="c1055-109">Tek bir değer yerine değerleri dizisi</span><span class="sxs-lookup"><span data-stu-id="c1055-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="c1055-110">A [Date veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) değer veya tarih ve saat değeri olarak yorumlanan dize</span><span class="sxs-lookup"><span data-stu-id="c1055-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="c1055-111">Bir nesne türü <xref:System.DBNull>, eksik ya da var olmayan verileri temsil eder</span><span class="sxs-lookup"><span data-stu-id="c1055-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="c1055-112">Türetilen bir özel durum nesnesi <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="c1055-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="c1055-113">[Hiçbir şey](../../../../visual-basic/language-reference/nothing.md), diğer bir deyişle, bir nesne değişkenine şu anda atanır</span><span class="sxs-lookup"><span data-stu-id="c1055-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="c1055-114">Bir sayı veya sayı olarak yorumlanan dize</span><span class="sxs-lookup"><span data-stu-id="c1055-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="c1055-115">Bir başvuru türü (örneğin, bir dize, dizi, temsilci veya sınıf türü)</span><span class="sxs-lookup"><span data-stu-id="c1055-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="c1055-116">Bu işlevler, bir işlem veya yordam için geçersiz bir değer göndererek önlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1055-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="c1055-117">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="c1055-117">TypeOf Operator</span></span>  
 <span data-ttu-id="c1055-118">Ayrıca [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md) bir nesne değişkeninin bir özel veri türü için şu anda başvurmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="c1055-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="c1055-119">`TypeOf`... `Is` ifadeyi hesaplar için `True` işlenenin çalışma zamanı tür türetilir veya belirtilen türe uygular.</span><span class="sxs-lookup"><span data-stu-id="c1055-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="c1055-120">Aşağıdaki örnekte `TypeOf` değer ve başvuru türlerine başvuran nesne değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="c1055-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="c1055-121">Yukarıdaki örnekte aşağıdaki satırları Yazar **hata ayıklama** penceresi:</span><span class="sxs-lookup"><span data-stu-id="c1055-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="c1055-122">Nesne değişkeni `num` türü verilere başvuran `Integer`, ve `frm` sınıfın bir nesneye başvuruyor <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="c1055-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="c1055-123">Nesne dizileri</span><span class="sxs-lookup"><span data-stu-id="c1055-123">Object Arrays</span></span>  
 <span data-ttu-id="c1055-124">Bildirme ve bir dizi kullanın `Object` değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="c1055-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="c1055-125">Çeşitli veri türleri ve nesne sınıflarını işlemek gerektiğinde bu faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1055-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="c1055-126">Bir dizideki tüm öğeler aynı bildirilen veri türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1055-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="c1055-127">Bu veri türü olarak bildirme `Object` , nesneleri depolamak ve diğer veri türleri dizisi birlikte örnekleri sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1055-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1055-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1055-128">See also</span></span>

- [<span data-ttu-id="c1055-129">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c1055-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c1055-130">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="c1055-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="c1055-131">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="c1055-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c1055-132">Nasıl yapılır: Bir nesnenin geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="c1055-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="c1055-133">Nasıl yapılır: Bir nesne değişkeninin için hangi türe başvurduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="c1055-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="c1055-134">Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="c1055-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="c1055-135">Nasıl yapılır: İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="c1055-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="c1055-136">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c1055-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
