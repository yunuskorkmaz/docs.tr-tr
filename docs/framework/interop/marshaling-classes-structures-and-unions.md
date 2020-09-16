---
title: Sınıflar, Yapılar ve Birleşimleri Hazırlama
description: Sınıfların, yapıların ve birleşimlerin nasıl hazırlanacağını gözden geçirin. Sıralama sınıflarının örneklerini, iç içe yapıları olan yapıları, yapı dizilerini ve birleşimleri görüntüleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 25de633faabb1424bcf5e618cc5ca129e61c5fca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547876"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="1b8a3-104">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1b8a3-104">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="1b8a3-105">Sınıflar ve yapılar .NET Framework benzerdir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-105">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="1b8a3-106">Her ikisinde de alanlar, Özellikler ve olaylar olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-106">Both can have fields, properties, and events.</span></span> <span data-ttu-id="1b8a3-107">Statik ve statik olmayan yöntemlere de sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-107">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="1b8a3-108">Bir önemli farkı, yapıların değer türleri ve sınıfların başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-108">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="1b8a3-109">Aşağıdaki tablo sınıflar, yapılar ve birleşimler için sıralama seçeneklerini listeler; kullanımlarını açıklar; ve buna karşılık gelen platform çağırma örneğine bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-109">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="1b8a3-110">Tür</span><span class="sxs-lookup"><span data-stu-id="1b8a3-110">Type</span></span>|<span data-ttu-id="1b8a3-111">Description</span><span class="sxs-lookup"><span data-stu-id="1b8a3-111">Description</span></span>|<span data-ttu-id="1b8a3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b8a3-112">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="1b8a3-113">Değere göre sınıf.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-113">Class by value.</span></span>|<span data-ttu-id="1b8a3-114">Tamsayı üyeleri olan bir sınıfı, yönetilen durum gibi bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-114">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="1b8a3-115">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-115">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="1b8a3-116">Değere göre yapı.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-116">Structure by value.</span></span>|<span data-ttu-id="1b8a3-117">Yapıları parametrelerde olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-117">Passes structures as In parameters.</span></span>|[<span data-ttu-id="1b8a3-118">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-118">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="1b8a3-119">Başvuruya göre yapı.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-119">Structure by reference.</span></span>|<span data-ttu-id="1b8a3-120">Yapıları ın/out parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-120">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="1b8a3-121">[OSInfo örneği](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b8a3-121">[OSInfo sample](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="1b8a3-122">İç içe yapılar (düzleştirilmiş) ile yapı.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-122">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="1b8a3-123">Yönetilmeyen işlevde iç içe yapılar içeren bir yapıyı temsil eden bir sınıf geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-123">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="1b8a3-124">Yapı, yönetilen prototipde bir büyük yapıya düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-124">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="1b8a3-125">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-125">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="1b8a3-126">Başka bir yapıya işaretçi içeren yapı.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-126">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="1b8a3-127">İkinci bir yapıya bir işaretçi içeren bir yapıyı üye olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-127">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="1b8a3-128">Yapılar Örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-128">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="1b8a3-129">Değere göre tamsayılar içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-129">Array of structures with integers by value.</span></span>|<span data-ttu-id="1b8a3-130">Yalnızca tamsayı içeren bir yapı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-130">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="1b8a3-131">Dizi üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-131">Members of the array can be changed.</span></span>|[<span data-ttu-id="1b8a3-132">Diziler Örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-132">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="1b8a3-133">Başvuruya göre tamsayılar ve dizeler içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-133">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="1b8a3-134">Out parametresi olarak tamsayılar ve dizeler içeren bir yapı dizisini geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-134">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="1b8a3-135">Çağrılan işlev dizi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-135">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="1b8a3-136">Outarrayofyapılar örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-136">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="1b8a3-137">Değer türleri olan birleşimler.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-137">Unions with value types.</span></span>|<span data-ttu-id="1b8a3-138">Birleşimleri değer türleriyle geçirir (tamsayı ve çift).</span><span class="sxs-lookup"><span data-stu-id="1b8a3-138">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="1b8a3-139">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-139">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="1b8a3-140">Karışık Türler içeren birleşimler.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-140">Unions with mixed types.</span></span>|<span data-ttu-id="1b8a3-141">Birleşimleri karışık türler (tamsayı ve dize) ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-141">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="1b8a3-142">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-142">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="1b8a3-143">Platforma özgü düzen ile struct.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-143">Struct with platform-specific layout.</span></span>|<span data-ttu-id="1b8a3-144">Yerel paketleme tanımlarına sahip bir tür geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-144">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="1b8a3-145">Platform örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-145">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="1b8a3-146">Yapıda null değerler.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-146">Null values in structure.</span></span>|<span data-ttu-id="1b8a3-147">Değer türüne başvuru yerine bir null başvurusu (Visual Basic**hiçbir şey** ) geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-147">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="1b8a3-148">[HandleRef örneği](/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1b8a3-148">[HandleRef sample](/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="1b8a3-149">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-149">Structures sample</span></span>

<span data-ttu-id="1b8a3-150">Bu örnek, ikinci yapıya işaret eden bir yapının nasıl geçirileceğini, gömülü bir yapıya sahip bir yapının nasıl geçirileceğini ve bir yapının gömülü dizi ile nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-150">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="1b8a3-151">Yapılar örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-151">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="1b8a3-152">**Teststructsöylemek** PinvokeLib.dll 'dan verildi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-152">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="1b8a3-153">**TestStructInStruct3** PinvokeLib.dll dışarıya verildi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-153">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="1b8a3-154">**Testarraysöylemek** PinvokeLib.dll 'dan verildi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-154">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="1b8a3-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlevler ve dört yapı için uygulamalar içeren özel bir yönetilmeyen kitaplıktır: **MyPerson**, **MyPerson2**, **MyPerson3**ve **MyArrayStruct**.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="1b8a3-156">Bu yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-156">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="1b8a3-157">Yönetilen `MyPerson` , `MyPerson2` , `MyPerson3` ve `MyArrayStruct` yapıları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-157">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="1b8a3-158">`MyPerson` yalnızca dize üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-158">`MyPerson` contains only string members.</span></span> <span data-ttu-id="1b8a3-159">[Karakter kümesi](specifying-a-character-set.md) alanı yönetilmeyen işleve GEÇIRILDIĞINDE dizeleri ANSI biçimine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-159">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="1b8a3-160">`MyPerson2` yapıya bir **IntPtr** içerir `MyPerson` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-160">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="1b8a3-161">.NET Framework uygulamalar, kod **güvensiz**olarak işaretlenmedikçe işaretçileri kullanmadığı Için, **IntPtr** türü özgün işaretçinin yönetilmeyen yapıya göre yerini alır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-161">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="1b8a3-162">`MyPerson3``MyPerson`gömülü yapı olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-162">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="1b8a3-163">Başka bir yapıda gömülü bir yapı, gömülü yapının öğeleri doğrudan ana yapıya girilerek düzleştirilir veya bu örnekte yapıldığı gibi gömülü bir yapı olarak bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-163">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="1b8a3-164">`MyArrayStruct` bir tamsayılar dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-164">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="1b8a3-165"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini dizideki öğelerin sayısını göstermek Için kullanılan **ByValArray**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-165">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="1b8a3-166">Bu örnekteki tüm yapılar için, <xref:System.Runtime.InteropServices.StructLayoutAttribute> üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak için özniteliği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-166">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="1b8a3-167">`NativeMethods`Sınıfı `TestStructInStruct` ,, `TestStructInStruct3` ve `TestArrayInStruct` sınıfı tarafından çağrılan yöntemler için yönetilen prototürler içerir `App` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-167">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="1b8a3-168">Her prototip, aşağıdaki gibi tek bir parametre bildirir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-168">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="1b8a3-169">`TestStructInStruct` parametresi olarak yazmak için bir başvuru bildirir `MyPerson2` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-169">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="1b8a3-170">`TestStructInStruct3` türü `MyPerson3` parametresi olarak bildirir ve parametreyi değere göre geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-170">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="1b8a3-171">`TestArrayInStruct` parametresi olarak yazmak için bir başvuru bildirir `MyArrayStruct` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-171">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="1b8a3-172">Parametreler **ref** (Visual Basic içinde**ByRef** ) anahtar sözcüğü içermiyorsa, yöntemlere bağımsız değişken olarak geçirilen yapılar değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-172">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="1b8a3-173">Örneğin, `TestStructInStruct` yöntemi bir başvurusu (bir adresin değeri) türünde bir nesneye, `MyPerson2` yönetilmeyen koda geçirir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-173">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="1b8a3-174">' A işaret eden yapıyı değiştirmek için `MyPerson2` örnek, belirtilen boyutun bir arabelleğini oluşturur ve ve yöntemlerini birleştirerek adresini döndürür <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-174">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="1b8a3-175">Ardından örnek, yönetilen yapının içeriğini yönetilmeyen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-175">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="1b8a3-176">Son olarak, örnek, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> yönetilmeyen arabellekteki verileri yönetilen bir nesneye ve <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yönetilmeyen bellek bloğunu serbest bırakma yöntemine göre sıralamak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-176">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="1b8a3-177">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="1b8a3-177">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="1b8a3-178">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="1b8a3-178">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="1b8a3-179">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-179">FindFile sample</span></span>

<span data-ttu-id="1b8a3-180">Bu örnek, yönetilmeyen bir işleve ikinci, gömülü bir yapı içeren bir yapının nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-180">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="1b8a3-181">Ayrıca, <xref:System.Runtime.InteropServices.MarshalAsAttribute> yapı içinde sabit uzunluklu bir dizi bildirmek için özniteliği nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-181">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="1b8a3-182">Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-182">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="1b8a3-183">Düzleştirilmemiş gömülü bir yapının örneği için bkz. [yapılar örneği](/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1b8a3-183">For a sample of an embedded structure that is not flattened, see [Structures Sample](/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="1b8a3-184">FindFile örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-184">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="1b8a3-185">Kernel32.dll 'den dışarıya aktarılmış **FindFirstFile** .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-185">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="1b8a3-186">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-186">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="1b8a3-187">Bu örnekte, `FindData` sınıfı özgün yapıdaki her öğe için karşılık gelen bir veri üyesini ve katıştırılmış yapıyı içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-187">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="1b8a3-188">İki orijinal karakter arabelleği yerine, sınıf yerine dizeler koyar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-188">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="1b8a3-189">**MarshalAsAttribute** numaralandırmayı, <xref:System.Runtime.InteropServices.UnmanagedType> yönetilmeyen yapılar içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek için kullanılan **ByValTStr**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-189">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="1b8a3-190">`NativeMethods`Sınıfı, `FindFirstFile` `FindData` sınıfının bir parametre olarak geçişini sağlayan, yönetilen bir prototipi içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-190">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="1b8a3-191">Parametre, <xref:System.Runtime.InteropServices.InAttribute> ve öznitelikleri ile bildirilmelidir <xref:System.Runtime.InteropServices.OutAttribute> çünkü başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-191">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="1b8a3-192">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="1b8a3-192">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="1b8a3-193">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="1b8a3-193">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="1b8a3-194">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-194">Unions sample</span></span>

<span data-ttu-id="1b8a3-195">Bu örnek, yalnızca değer türlerini içeren yapıların ve bir değer türü içeren yapıların ve bir birleşim bekleyen yönetilmeyen bir işleve parametre olarak dize olarak nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-195">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="1b8a3-196">Birleşim, iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-196">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="1b8a3-197">Birleşimler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-197">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="1b8a3-198">**TestUnion** PinvokeLib.dll 'dan verildi.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-198">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="1b8a3-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlev için bir uygulama ve **MyUnion** ve **MYUNION2**olmak üzere iki birleşim içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="1b8a3-200">Birleşimler aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-200">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="1b8a3-201">Yönetilen kodda birleşimler yapılar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-201">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="1b8a3-202">`MyUnion`Yapı, üyeleri olarak iki değer türü içerir: tamsayı ve çift.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-202">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="1b8a3-203"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Özniteliği her bir veri üyesinin kesin konumunu denetlemek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-203">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="1b8a3-204"><xref:System.Runtime.InteropServices.FieldOffsetAttribute>Özniteliği, bir birleşimin yönetilmeyen gösterimi içindeki alanların fiziksel konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-204">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="1b8a3-205">Her iki üyenin de aynı fark değerlerine sahip olduğuna dikkat edin, bu nedenle Üyeler aynı bellek parçasını tanımlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-205">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="1b8a3-206">`MyUnion2_1` ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-206">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="1b8a3-207">Yönetilen kodda, değer türleri ve başvuru türlerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-207">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="1b8a3-208">Bu örnek, çağıranın aynı yönetilmeyen işlevi çağırırken her iki türü de kullanmasını sağlamak için yöntem aşırı yüklemesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-208">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="1b8a3-209">Düzeni `MyUnion2_1` açıktır ve kesin bir fark değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-209">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="1b8a3-210">Buna karşılık, `MyUnion2_2` Başvuru türlerinde açık mizanpajlara izin verilmediğinden sıralı bir düzene sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-210">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="1b8a3-211"><xref:System.Runtime.InteropServices.MarshalAsAttribute>Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> UNION 'nin yönetilmeyen gösterimi içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek Için kullanılan **ByValTStr**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-211">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="1b8a3-212">`NativeMethods`Sınıfı ve yöntemlerinin prototiplerini içerir `TestUnion` `TestUnion2` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-212">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="1b8a3-213">`TestUnion2` , parametreleri bildirmek için aşırı yüklendi `MyUnion2_1` `MyUnion2_2` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-213">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="1b8a3-214">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="1b8a3-214">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="1b8a3-215">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="1b8a3-215">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="1b8a3-216">Platform örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-216">Platform sample</span></span>

<span data-ttu-id="1b8a3-217">Bazı senaryolarda `struct` ve `union` düzenler hedeflenen platforma bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-217">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="1b8a3-218">Örneğin, [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) BIR com senaryosunda tanımlandığı zaman türü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-218">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="1b8a3-219">Yukarıdaki, `struct` türün bellek yerleşimini etkileyen Windows üstbilgileri ile bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-219">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="1b8a3-220">Yönetilen bir ortamda tanımlandığında, yerel kodla düzgün şekilde birlikte çalışmak için bu düzen ayrıntılarının olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-220">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="1b8a3-221">Bu türün 32 bitlik bir işlemde doğru yönetilen tanımı:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-221">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="1b8a3-222">64 bit süreçte boyut *ve* alan uzaklıkları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-222">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="1b8a3-223">Doğru düzen:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-223">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="1b8a3-224">Bir birlikte çalışma senaryosunda yerel düzeni doğru şekilde düşünmeyen hata rastgele kilitlenmeler veya daha kötü hesaplamalar, yanlış hesaplamalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-224">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="1b8a3-225">Varsayılan olarak, .NET derlemeleri .NET çalışma zamanının 32-bit ve 64 bit sürümünde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-225">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="1b8a3-226">Uygulamanın, önceki tanımlardan hangisinin kullanılacağına karar vermek için çalışma zamanına kadar beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-226">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="1b8a3-227">Aşağıdaki kod parçacığı, çalışma zamanında 32-bit ve 64 bit tanım arasında nasıl seçim yapılacağı hakkında bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-227">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```csharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="1b8a3-228">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-228">SysTime sample</span></span>

<span data-ttu-id="1b8a3-229">Bu örnek, bir sınıfa işaretçi bekleyen yönetilmeyen bir işleve bir işaretçinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-229">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="1b8a3-230">SysTime örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-230">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="1b8a3-231">Kernel32.dll 'tan alınan **GetSystemTime** .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-231">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="1b8a3-232">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-232">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="1b8a3-233">Bu örnekte, `SystemTime` sınıfı sınıf üyeleri olarak temsil edilen orijinal yapının öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-233">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="1b8a3-234"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-234">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="1b8a3-235">`NativeMethods`Sınıfı, `GetSystemTime` `SystemTime` Varsayılan olarak sınıfı bir ın/out parametresi olarak ileten yönteminin yönetilen bir prototipini içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-235">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="1b8a3-236">Parametre, <xref:System.Runtime.InteropServices.InAttribute> ve öznitelikleri ile bildirilmelidir <xref:System.Runtime.InteropServices.OutAttribute> çünkü başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-236">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="1b8a3-237">Çağıranın sonuçları alması için, bu [yönlü özniteliklerin](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-237">For the caller to receive the results, these [directional attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="1b8a3-238">`App`Sınıfı, sınıfının yeni bir örneğini oluşturur `SystemTime` ve veri alanlarına erişir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-238">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="1b8a3-239">Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="1b8a3-239">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="1b8a3-240">OutArrayOfStructs örneği</span><span class="sxs-lookup"><span data-stu-id="1b8a3-240">OutArrayOfStructs sample</span></span>

<span data-ttu-id="1b8a3-241">Bu örnek, yönetilmeyen bir işleve tamsayı ve dizeler içeren bir yapı dizisinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-241">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="1b8a3-242">Bu örnek, <xref:System.Runtime.InteropServices.Marshal> sınıfını kullanarak ve güvenli olmayan kod kullanarak yerel bir işlevin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-242">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="1b8a3-243">Bu örnek, kaynak dosyalarında de sağlanmış olan [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll)bir sarmalayıcı işlevleri ve platform çağırır kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-243">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="1b8a3-244">`TestOutArrayOfStructs`İşlevi ve `MYSTRSTRUCT2` yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-244">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="1b8a3-245">Yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-245">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="1b8a3-246">`MyStruct`Sınıf, ANSI karakterlerinden oluşan bir dize nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-246">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="1b8a3-247"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>Alan ANSI biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-247">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="1b8a3-248">`MyUnsafeStruct`, <xref:System.IntPtr> bir dize yerine tür içeren bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-248">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="1b8a3-249">`NativeMethods`Sınıfı, aşırı yüklenmiş `TestOutArrayOfStructs` prototip metodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-249">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="1b8a3-250">Bir yöntem parametre olarak bir işaretçi bildirirse, sınıf `unsafe` anahtar sözcüğüyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-250">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="1b8a3-251">Visual Basic güvenli olmayan kod kullanamadığından, aşırı yüklenmiş yöntem, güvensiz değiştirici ve `MyUnsafeStruct` Yapı gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-251">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="1b8a3-252">`App`Sınıfı, `UsingMarshaling` diziyi iletmek için gereken tüm görevleri gerçekleştiren yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-252">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="1b8a3-253">Dizi `out` ( `ByRef` Visual Basic) anahtar sözcüğüyle işaretlenir ve bu, verilerin çağrıdan çağırana 'e geçtiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-253">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="1b8a3-254">Uygulama aşağıdaki <xref:System.Runtime.InteropServices.Marshal> sınıf yöntemlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1b8a3-254">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="1b8a3-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> yönetilmeyen arabellekteki verileri yönetilen bir nesneye sıralama.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="1b8a3-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> yapıdaki dizeler için ayrılan belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="1b8a3-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> dizi için ayrılan belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="1b8a3-258">Daha önce belirtildiği gibi, C# güvenli olmayan koda Izin veriyor ve Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-258">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="1b8a3-259">C# örneğinde, `UsingUnsafePointer` <xref:System.Runtime.InteropServices.Marshal> yapıyı içeren diziyi geri geçirmek için sınıfı yerine işaretçiler kullanan alternatif bir yöntem uygulamasıdır `MyUnsafeStruct` .</span><span class="sxs-lookup"><span data-stu-id="1b8a3-259">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="1b8a3-260">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="1b8a3-260">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="1b8a3-261">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="1b8a3-261">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="1b8a3-262">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b8a3-262">See also</span></span>

- [<span data-ttu-id="1b8a3-263">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="1b8a3-263">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="1b8a3-264">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1b8a3-264">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="1b8a3-265">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="1b8a3-265">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
