---
description: 'Hakkında daha fazla bilgi edinin: nesne veri türü'
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
ms.openlocfilehash: b1f169e4e590335a0879f5ecd9b68507a3fa2ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792160"
---
# <a name="object-data-type"></a><span data-ttu-id="5d2c7-103">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5d2c7-103">Object Data Type</span></span>

<span data-ttu-id="5d2c7-104">Nesnelere başvuran adresleri tutar.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-104">Holds addresses that refer to objects.</span></span> <span data-ttu-id="5d2c7-105">Herhangi bir başvuru türünü (String, Array, Class veya Interface) bir `Object` değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-105">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="5d2c7-106">Bir `Object` değişken, herhangi bir değer türünün (sayısal, `Boolean` , `Char` ,, `Date` Yapı veya sabit listesi) verilerine de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-106">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>

## <a name="remarks"></a><span data-ttu-id="5d2c7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d2c7-107">Remarks</span></span>

<span data-ttu-id="5d2c7-108">`Object`Veri türü, uygulamanızın tanıdığı herhangi bir nesne örneği de dahil olmak üzere herhangi bir veri türünün verilerini işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-108">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="5d2c7-109">`Object`Derleme zamanında, değişkenin işaret edebilecekleri veri türünü bilmediğinizde ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-109">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>

<span data-ttu-id="5d2c7-110">Öğesinin varsayılan değeri `Object` `Nothing` (null başvurusu).</span><span class="sxs-lookup"><span data-stu-id="5d2c7-110">The default value of `Object` is `Nothing` (a null reference).</span></span>

## <a name="data-types"></a><span data-ttu-id="5d2c7-111">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="5d2c7-111">Data Types</span></span>

<span data-ttu-id="5d2c7-112">Bir değişkene herhangi bir veri türü için değişken, sabit veya ifade atayabilirsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-112">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="5d2c7-113">Şu anda başvurduğu bir değişkenin veri türünü öğrenmek için `Object` , <xref:System.Type.GetTypeCode%2A> sınıfının yöntemini kullanabilirsiniz <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-113">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5d2c7-114">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-114">The following example illustrates this.</span></span>

```vb
Dim myObject As Object
' Suppose myObject has now had something assigned to it.
Dim datTyp As Integer
datTyp = Type.GetTypeCode(myObject.GetType())
```

<span data-ttu-id="5d2c7-115">`Object`Veri türü bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-115">The `Object` data type is a reference type.</span></span> <span data-ttu-id="5d2c7-116">Ancak, Visual Basic bir `Object` değişkeni bir değer türünün verilerine başvurduğunda değer türü olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-116">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>

## <a name="storage"></a><span data-ttu-id="5d2c7-117">Depolama</span><span class="sxs-lookup"><span data-stu-id="5d2c7-117">Storage</span></span>

<span data-ttu-id="5d2c7-118">Başvurduğu veri türü ne olursa olsun, bir `Object` değişken veri değerinin kendisini içermez, bunun yerine değer için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-118">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="5d2c7-119">Bilgisayar belleğinde her zaman dört bayt kullanır, ancak bu, değişkenin değerini temsil eden veriler için depolama alanı içermez.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-119">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="5d2c7-120">Verileri bulmak için işaretçiyi kullanan kod nedeniyle, `Object` değer türlerini tutan değişkenlerin açık olarak belirlenmiş değişkenlerle erişimi biraz daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-120">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="5d2c7-121">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="5d2c7-121">Programming Tips</span></span>

- <span data-ttu-id="5d2c7-122">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="5d2c7-122">**Interop Considerations.**</span></span> <span data-ttu-id="5d2c7-123">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabiriminiz varsa, diğer ortamlardaki işaretçi türlerinin Visual Basic türüyle uyumlu olmadığını göz önünde bulundurun `Object` .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>

- <span data-ttu-id="5d2c7-124">**Mının.**</span><span class="sxs-lookup"><span data-stu-id="5d2c7-124">**Performance.**</span></span> <span data-ttu-id="5d2c7-125">Türü ile bildirdiğiniz bir değişken, `Object` herhangi bir nesneye başvuru içermesi için yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-125">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="5d2c7-126">Ancak, bu tür bir değişkende bir yöntemi veya özelliği çağırdığınızda, her zaman *geç bağlamaya* (çalışma zamanında) tabi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-126">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="5d2c7-127">*Erken bağlamayı* zorlamak için (derleme zamanında) ve daha iyi performans, değişkeni belirli bir sınıf adıyla bildirin veya belirli bir veri türüne atayın.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-127">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>

  <span data-ttu-id="5d2c7-128">Bir nesne değişkeni bildirdiğinizde, örneğin Genelleştirilmiş tür yerine belirli bir sınıf türü kullanmayı deneyin <xref:System.OperatingSystem> `Object` .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-128">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="5d2c7-129"><xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Control> Özelliklerine ve yöntemlerine erişebilmek için, yerine, kullanılabilir olan en özel sınıfı da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-129">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="5d2c7-130">Kullanılabilir sınıf adlarını bulmak için genellikle **nesne tarayıcısı** **sınıfları** listesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-130">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>

- <span data-ttu-id="5d2c7-131">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="5d2c7-131">**Widening.**</span></span> <span data-ttu-id="5d2c7-132">Tüm veri türleri ve tüm başvuru türleri veri türüne göre genişledir `Object` .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-132">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="5d2c7-133">Bu, herhangi `Object` bir türü bir hatayla karşılaşmadan dönüştürmek üzere dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5d2c7-133">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

  <span data-ttu-id="5d2c7-134">Ancak, değer türleri arasında dönüştürme yaparsanız `Object` , Visual Basic, yürütmeyi daha yavaş hale getiren *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-134">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>

- <span data-ttu-id="5d2c7-135">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="5d2c7-135">**Type Characters.**</span></span> <span data-ttu-id="5d2c7-136">`Object` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-136">`Object` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="5d2c7-137">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="5d2c7-137">**Framework Type.**</span></span> <span data-ttu-id="5d2c7-138">.NET Framework karşılık gelen tür <xref:System.Object?displayProperty=nameWithType> sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-138">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=nameWithType> class.</span></span>

## <a name="example"></a><span data-ttu-id="5d2c7-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d2c7-139">Example</span></span>

<span data-ttu-id="5d2c7-140">Aşağıdaki örnek, `Object` bir nesne örneğine işaret eden bir değişken gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-140">The following example illustrates an `Object` variable pointing to an object instance.</span></span>

```vb
Dim objDb As Object
Dim myCollection As New Collection()
' Suppose myCollection has now been populated.
objDb = myCollection.Item(1)
```

## <a name="see-also"></a><span data-ttu-id="5d2c7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2c7-141">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="5d2c7-142">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="5d2c7-142">Data Types</span></span>](index.md)
- [<span data-ttu-id="5d2c7-143">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5d2c7-143">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="5d2c7-144">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="5d2c7-144">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="5d2c7-145">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="5d2c7-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="5d2c7-146">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="5d2c7-146">How to: Determine Whether Two Objects Are Related</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="5d2c7-147">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="5d2c7-147">How to: Determine Whether Two Objects Are Identical</span></span>](../../programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
