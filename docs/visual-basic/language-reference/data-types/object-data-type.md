---
title: Nesne Veri Türü
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
ms.openlocfilehash: 14770e74a0169dba3a45a04845dd32323e6201e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415589"
---
# <a name="object-data-type"></a><span data-ttu-id="d47bd-102">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d47bd-102">Object Data Type</span></span>

<span data-ttu-id="d47bd-103">Nesnelere başvuran adresleri tutar.</span><span class="sxs-lookup"><span data-stu-id="d47bd-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="d47bd-104">Herhangi bir başvuru türünü (String, Array, Class veya Interface) bir `Object` değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d47bd-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="d47bd-105">Bir `Object` değişken, herhangi bir değer türünün (sayısal, `Boolean` , `Char` ,, `Date` Yapı veya sabit listesi) verilerine de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="d47bd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d47bd-106">Remarks</span></span>

<span data-ttu-id="d47bd-107">`Object`Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere herhangi bir veri türünün verilerini işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="d47bd-108">`Object`Derleme zamanında, değişkenin işaret edebilecekleri veri türünü bilmediğinizde ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="d47bd-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="d47bd-109">Öğesinin varsayılan değeri `Object` `Nothing` (null başvurusu).</span><span class="sxs-lookup"><span data-stu-id="d47bd-109">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="d47bd-110">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="d47bd-110">Data Types</span></span>

<span data-ttu-id="d47bd-111">Bir değişkene herhangi bir veri türü için değişken, sabit veya ifade atayabilirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="d47bd-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="d47bd-112">Şu anda başvurduğu bir değişkenin veri türünü öğrenmek için `Object` , <xref:System.Type.GetTypeCode%2A> sınıfının yöntemini kullanabilirsiniz <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d47bd-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d47bd-113">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-113">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="d47bd-114">`Object`Veri türü bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="d47bd-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="d47bd-115">Ancak, Visual Basic bir `Object` değişkeni bir değer türünün verilerine başvurduğunda değer türü olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="d47bd-116">Depolama</span><span class="sxs-lookup"><span data-stu-id="d47bd-116">Storage</span></span>

<span data-ttu-id="d47bd-117">Başvurduğu veri türü ne olursa olsun, bir `Object` değişken veri değerinin kendisini içermez, bunun yerine değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d47bd-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="d47bd-118">Bilgisayar belleğinde her zaman dört bayt kullanır, ancak bu, değişkenin değerini temsil eden veriler için depolama alanı içermez.</span><span class="sxs-lookup"><span data-stu-id="d47bd-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="d47bd-119">Verileri bulmak için işaretçiyi kullanan kod nedeniyle, `Object` değer türlerini tutan değişkenlerin açık olarak belirlenmiş değişkenlerle erişimi biraz daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="d47bd-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="d47bd-120">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="d47bd-120">Programming Tips</span></span>

- <span data-ttu-id="d47bd-121">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="d47bd-121">**Interop Considerations.**</span></span> <span data-ttu-id="d47bd-122">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabiriminiz varsa, diğer ortamlardaki işaretçi türlerinin Visual Basic türüyle uyumlu olmadığını göz önünde bulundurun `Object` .</span><span class="sxs-lookup"><span data-stu-id="d47bd-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="d47bd-123">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="d47bd-123">**Performance.**</span></span> <span data-ttu-id="d47bd-124">Türü ile bildirdiğiniz bir değişken, `Object` herhangi bir nesneye başvuru içermesi için yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="d47bd-125">Ancak, bu tür bir değişkende bir yöntemi veya özelliği çağırdığınızda, her zaman *geç bağlamaya* (çalışma zamanında) tabi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="d47bd-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="d47bd-126">*Erken bağlamayı* zorlamak için (derleme zamanında) ve daha iyi performans, değişkeni belirli bir sınıf adıyla bildirin veya belirli bir veri türüne atayın.</span><span class="sxs-lookup"><span data-stu-id="d47bd-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="d47bd-127">Bir nesne değişkeni bildirdiğinizde, örneğin Genelleştirilmiş tür yerine belirli bir sınıf türü kullanmayı deneyin <xref:System.OperatingSystem> `Object` .</span><span class="sxs-lookup"><span data-stu-id="d47bd-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="d47bd-128"><xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control> Özelliklerine ve yöntemlerine erişebilmek için, yerine, kullanılabilir olan en özel sınıfı da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="d47bd-129">Kullanılabilir sınıf adlarını bulmak için genellikle **nesne tarayıcısı** **sınıfları** listesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d47bd-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="d47bd-130">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="d47bd-130">**Widening.**</span></span> <span data-ttu-id="d47bd-131">Tüm veri türleri ve tüm başvuru türleri veri türüne göre genişledir `Object` .</span><span class="sxs-lookup"><span data-stu-id="d47bd-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="d47bd-132">Bu, herhangi `Object` bir türü bir hatayla karşılaşmadan dönüştürmek üzere dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d47bd-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="d47bd-133">Ancak, değer türleri arasında dönüştürme yaparsanız `Object` , Visual Basic, yürütmeyi daha yavaş hale getiren *kutulama* ve *kutudan*çıkarma adlı işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="d47bd-134">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="d47bd-134">**Type Characters.**</span></span> <span data-ttu-id="d47bd-135">`Object`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="d47bd-135">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="d47bd-136">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="d47bd-136">**Framework Type.**</span></span> <span data-ttu-id="d47bd-137">.NET Framework karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d47bd-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="d47bd-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="d47bd-138">Example</span></span>

<span data-ttu-id="d47bd-139">Aşağıdaki örnek, `Object` bir nesne örneğine işaret eden bir değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="d47bd-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="d47bd-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d47bd-140">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="d47bd-141">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="d47bd-141">Data Types</span></span>](index.md)
- [<span data-ttu-id="d47bd-142">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d47bd-142">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d47bd-143">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="d47bd-143">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d47bd-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="d47bd-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="d47bd-145">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="d47bd-145">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="d47bd-146">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="d47bd-146">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
