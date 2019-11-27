---
title: Nesne Değişkeni Değerleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 8b93063d2d97802b1a7fdbc93e01040ff3337753
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351796"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="f743d-102">Nesne Değişkeni Değerleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f743d-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="f743d-103">[Nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) değişkeni herhangi bir türdeki verilere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f743d-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="f743d-104">Bir `Object` değişkeninde depoladığınız değer bellekte başka bir yerde tutulur, ancak değişken verileri bir işaretçi tutar.</span><span class="sxs-lookup"><span data-stu-id="f743d-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="f743d-105">Nesne sınıflandırıcı Işlevleri</span><span class="sxs-lookup"><span data-stu-id="f743d-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="f743d-106">Visual Basic, aşağıdaki tabloda gösterildiği gibi, bir `Object` değişkeninin başvurduğu hakkında bilgi döndüren işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f743d-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f743d-107">İşlev</span><span class="sxs-lookup"><span data-stu-id="f743d-107">Function</span></span>|<span data-ttu-id="f743d-108">Nesne değişkeni öğesine başvuruyorsa true döndürür</span><span class="sxs-lookup"><span data-stu-id="f743d-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="f743d-109">Tek bir değer yerine bir değer dizisi</span><span class="sxs-lookup"><span data-stu-id="f743d-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="f743d-110">[Tarih veri türü](../../../../visual-basic/language-reference/data-types/date-data-type.md) değeri veya tarih ve saat değeri olarak yorumlanabilen bir dize</span><span class="sxs-lookup"><span data-stu-id="f743d-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="f743d-111">Eksik veya varolmayan verileri temsil eden <xref:System.DBNull>türünde bir nesne</span><span class="sxs-lookup"><span data-stu-id="f743d-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="f743d-112"><xref:System.Exception> türettiği bir özel durum nesnesi</span><span class="sxs-lookup"><span data-stu-id="f743d-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="f743d-113">[Hiçbir şey](../../../../visual-basic/language-reference/nothing.md)yok, başka bir deyişle, şu anda değişkene atanmış nesne yok</span><span class="sxs-lookup"><span data-stu-id="f743d-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="f743d-114">Sayı veya bir sayı olarak yorumlanabilecek dize</span><span class="sxs-lookup"><span data-stu-id="f743d-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="f743d-115">Bir başvuru türü (dize, dizi, temsilci veya sınıf türü gibi)</span><span class="sxs-lookup"><span data-stu-id="f743d-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="f743d-116">Bir işleme veya yordama geçersiz bir değer gönderilmesini önlemek için bu işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f743d-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="f743d-117">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="f743d-117">TypeOf Operator</span></span>  
 <span data-ttu-id="f743d-118">Bir nesne değişkeninin şu anda belirli bir veri türüne başvuruda bulunup bulunmadığını anlamak için [typeof işlecini](../../../../visual-basic/language-reference/operators/typeof-operator.md) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f743d-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="f743d-119">`TypeOf`...`Is` ifadesi, işlenenin çalışma zamanı türü belirtilen türden türetildiyse veya uyguluyorsa `True` olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f743d-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="f743d-120">Aşağıdaki örnek, değer ve başvuru türlerine başvuran nesne değişkenlerinde `TypeOf` kullanır.</span><span class="sxs-lookup"><span data-stu-id="f743d-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="f743d-121">Yukarıdaki örnek, **hata ayıklama** penceresine aşağıdaki satırları Yazar:</span><span class="sxs-lookup"><span data-stu-id="f743d-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="f743d-122">`num` nesne değişkeni `Integer`türündeki verileri ifade eder ve `frm` <xref:System.Windows.Forms.Form>bir nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="f743d-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="f743d-123">Nesne dizileri</span><span class="sxs-lookup"><span data-stu-id="f743d-123">Object Arrays</span></span>  
 <span data-ttu-id="f743d-124">Bir dizi `Object` değişken bildirebilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f743d-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="f743d-125">Bu, çeşitli veri türlerini ve nesne sınıflarını işlemeniz gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f743d-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="f743d-126">Bir dizideki tüm öğeler aynı tanımlanmış veri türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f743d-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="f743d-127">Bu veri türünü `Object` olarak bildirmek, nesneleri ve sınıf örneklerini dizideki diğer veri türleriyle birlikte depolamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f743d-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f743d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f743d-128">See also</span></span>

- [<span data-ttu-id="f743d-129">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f743d-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="f743d-130">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f743d-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="f743d-131">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="f743d-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="f743d-132">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma</span><span class="sxs-lookup"><span data-stu-id="f743d-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="f743d-133">Nasıl yapılır: Bir Nesne Değişkeninin Hangi Türe Başvurduğunu Belirleme</span><span class="sxs-lookup"><span data-stu-id="f743d-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="f743d-134">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f743d-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="f743d-135">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f743d-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="f743d-136">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="f743d-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
