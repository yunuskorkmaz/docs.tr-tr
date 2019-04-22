---
title: Nesne veri türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Object
- vb.Variant
helpviewer_keywords:
- object variables [Visual Basic], Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type [Visual Basic], reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
ms.openlocfilehash: 616110145db2796e05509094b1c023daacd68f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835576"
---
# <a name="object-data-type"></a><span data-ttu-id="543fe-102">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="543fe-102">Object Data Type</span></span>
<span data-ttu-id="543fe-103">Nesnelere atıfta adresleri tutar.</span><span class="sxs-lookup"><span data-stu-id="543fe-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="543fe-104">Herhangi bir başvuru türü (dize, dizi, sınıf veya arabirim) atayabileceğiniz bir `Object` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="543fe-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="543fe-105">Bir `Object` değişkeni ayrıca herhangi bir değer türünün veri başvuru (sayısal, `Boolean`, `Char`, `Date`, yapı ya da numaralandırma).</span><span class="sxs-lookup"><span data-stu-id="543fe-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="543fe-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="543fe-106">Remarks</span></span>  
 <span data-ttu-id="543fe-107">`Object` Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneğine dahil olmak üzere, herhangi bir veri türü veri işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="543fe-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="543fe-108">Kullanım `Object` derleme zamanında bilmediğinizde değişkeni hangi veri türü için işaret ediyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="543fe-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="543fe-109">Varsayılan değer olan `Object` olduğu `Nothing` (null bir başvuru).</span><span class="sxs-lookup"><span data-stu-id="543fe-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="543fe-110">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="543fe-110">Data Types</span></span>  
 <span data-ttu-id="543fe-111">Bir değişken, sabit veya herhangi bir veri türü ifadesi atayabilirsiniz bir `Object` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="543fe-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="543fe-112">Veri türünü belirlemek için bir `Object` değişkeni şu anda başvurur, kullanabileceğiniz <xref:System.Type.GetTypeCode%2A> yöntemi <xref:System.Type?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="543fe-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="543fe-113">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="543fe-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="543fe-114">`Object` Veri türü olan bir başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="543fe-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="543fe-115">Ancak, Visual Basic değerlendirir bir `Object` değişken olarak bir değer türü veri başvurduğunda bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="543fe-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="543fe-116">Depolama</span><span class="sxs-lookup"><span data-stu-id="543fe-116">Storage</span></span>  
 <span data-ttu-id="543fe-117">Hangi veri türü başvurduğu için bir `Object` değişkeni değiştiremeyeceğinize, ancak bunun yerine bir işaretçi değerine veri değeri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="543fe-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="543fe-118">Her zaman bilgisayar belleğinde dört bayt kullanır, ancak bu değişkenin değerini temsil eden veriler için depolama içermez.</span><span class="sxs-lookup"><span data-stu-id="543fe-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="543fe-119">İşaretçi verileri bulmak için kullandığı kodu nedeniyle `Object` değişkenleri değer türleri tutarak daha açıkça belirlenmiş değişkenlere erişmek biraz daha yavaş.</span><span class="sxs-lookup"><span data-stu-id="543fe-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="543fe-120">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="543fe-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="543fe-121">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="543fe-121">**Interop Considerations.**</span></span> <span data-ttu-id="543fe-122">Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, diğer ortamlarda işaretçi türleri, Visual Basic ile uyumlu olmadığını aklınızda bulundurun `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="543fe-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="543fe-123">**Performans.**</span><span class="sxs-lookup"><span data-stu-id="543fe-123">**Performance.**</span></span> <span data-ttu-id="543fe-124">Bir değişken bildirmek ile `Object` türü olan herhangi bir nesneye bir başvuru içermesi için yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="543fe-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="543fe-125">Ancak, bir metot veya özellik bu tür bir değişken üzerinde çağırdığınızda, her zaman ücretler *geç bağlama* (çalışma zamanında).</span><span class="sxs-lookup"><span data-stu-id="543fe-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="543fe-126">Zorlamak için *erken bağlama* (derleme zamanında) ve daha iyi performans, belirli bir sınıf adı ile bir değişken bildirmek veya belirli bir veri türüne.</span><span class="sxs-lookup"><span data-stu-id="543fe-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="543fe-127">Örneğin, belirli bir sınıf türü kullanmak bir nesne değişkeni bildirdiğinizde deneyin <xref:System.OperatingSystem>, genelleştirilmiş yerine `Object` türü.</span><span class="sxs-lookup"><span data-stu-id="543fe-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="543fe-128">Kullanılabilir gibi en belirgin sınıfı de kullanmalısınız <xref:System.Windows.Forms.TextBox> yerine <xref:System.Windows.Forms.Control>, böylece özelliklerine ve yöntemlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="543fe-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="543fe-129">Genellikle kullanabileceğiniz **sınıfları** listesinde **Nesne Tarayıcısı** kullanılabilir sınıf adlarını bulmak için.</span><span class="sxs-lookup"><span data-stu-id="543fe-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="543fe-130">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="543fe-130">**Widening.**</span></span> <span data-ttu-id="543fe-131">Tüm veri türleri ve tüm başvuru türleri için genişletmek `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="543fe-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="543fe-132">Yani tüm türüne dönüştürebilir `Object` karşılaşmadan bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="543fe-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
     <span data-ttu-id="543fe-133">Ancak, değer türleri arasında dönüştürürseniz ve `Object`, Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma*, daha yavaş yürütme olun.</span><span class="sxs-lookup"><span data-stu-id="543fe-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="543fe-134">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="543fe-134">**Type Characters.**</span></span> <span data-ttu-id="543fe-135">`Object` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="543fe-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="543fe-136">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="543fe-136">**Framework Type.**</span></span> <span data-ttu-id="543fe-137">.NET Framework içinde karşılık gelen türü <xref:System.Object?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="543fe-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="543fe-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="543fe-138">Example</span></span>  
 <span data-ttu-id="543fe-139">Aşağıdaki örnekte bir `Object` işaret eden bir nesne örneğine değişkeni.</span><span class="sxs-lookup"><span data-stu-id="543fe-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="543fe-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="543fe-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="543fe-141">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="543fe-141">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="543fe-142">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="543fe-142">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="543fe-143">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="543fe-143">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="543fe-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="543fe-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="543fe-145">Nasıl yapılır: İki nesnenin ilgili olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="543fe-145">How to: Determine Whether Two Objects Are Related</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="543fe-146">Nasıl yapılır: İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="543fe-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
