---
title: Sınıflar, Yapılar ve Birleşimleri Hazırlama
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
ms.openlocfilehash: 708ed6a232950cb69796f105f6f198749ed53a24
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200021"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="12351-102">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="12351-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="12351-103">Sınıflar ve yapılar .NET Framework benzerdir.</span><span class="sxs-lookup"><span data-stu-id="12351-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="12351-104">Her ikisinde de alanlar, Özellikler ve olaylar olabilir.</span><span class="sxs-lookup"><span data-stu-id="12351-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="12351-105">Statik ve statik olmayan yöntemlere de sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="12351-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="12351-106">Bir önemli farkı, yapıların değer türleri ve sınıfların başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="12351-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="12351-107">Aşağıdaki tablo sınıflar, yapılar ve birleşimler için sıralama seçeneklerini listeler; kullanımlarını açıklar; ve buna karşılık gelen platform çağırma örneğine bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="12351-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="12351-108">Tür</span><span class="sxs-lookup"><span data-stu-id="12351-108">Type</span></span>|<span data-ttu-id="12351-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12351-109">Description</span></span>|<span data-ttu-id="12351-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="12351-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="12351-111">Değere göre sınıf.</span><span class="sxs-lookup"><span data-stu-id="12351-111">Class by value.</span></span>|<span data-ttu-id="12351-112">Tamsayı üyeleri olan bir sınıfı, yönetilen durum gibi bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="12351-113">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="12351-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="12351-114">Değere göre yapı.</span><span class="sxs-lookup"><span data-stu-id="12351-114">Structure by value.</span></span>|<span data-ttu-id="12351-115">Yapıları parametrelerde olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="12351-116">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="12351-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="12351-117">Başvuruya göre yapı.</span><span class="sxs-lookup"><span data-stu-id="12351-117">Structure by reference.</span></span>|<span data-ttu-id="12351-118">Yapıları ın/out parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="12351-119">[OSInfo örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12351-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="12351-120">İç içe yapılar (düzleştirilmiş) ile yapı.</span><span class="sxs-lookup"><span data-stu-id="12351-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="12351-121">Yönetilmeyen işlevde iç içe yapılar içeren bir yapıyı temsil eden bir sınıf geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="12351-122">Yapı, yönetilen prototipde bir büyük yapıya düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="12351-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="12351-123">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="12351-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="12351-124">Başka bir yapıya işaretçi içeren yapı.</span><span class="sxs-lookup"><span data-stu-id="12351-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="12351-125">İkinci bir yapıya bir işaretçi içeren bir yapıyı üye olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="12351-126">Yapılar Örneği</span><span class="sxs-lookup"><span data-stu-id="12351-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="12351-127">Değere göre tamsayılar içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="12351-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="12351-128">Yalnızca tamsayı içeren bir yapı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="12351-129">Dizi üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="12351-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="12351-130">Diziler Örneği</span><span class="sxs-lookup"><span data-stu-id="12351-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="12351-131">Başvuruya göre tamsayılar ve dizeler içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="12351-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="12351-132">Out parametresi olarak tamsayılar ve dizeler içeren bir yapı dizisini geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="12351-133">Çağrılan işlev dizi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="12351-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="12351-134">Outarrayofyapılar örneği</span><span class="sxs-lookup"><span data-stu-id="12351-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="12351-135">Değer türleri olan birleşimler.</span><span class="sxs-lookup"><span data-stu-id="12351-135">Unions with value types.</span></span>|<span data-ttu-id="12351-136">Birleşimleri değer türleriyle geçirir (tamsayı ve çift).</span><span class="sxs-lookup"><span data-stu-id="12351-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="12351-137">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="12351-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="12351-138">Karışık Türler içeren birleşimler.</span><span class="sxs-lookup"><span data-stu-id="12351-138">Unions with mixed types.</span></span>|<span data-ttu-id="12351-139">Birleşimleri karışık türler (tamsayı ve dize) ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="12351-140">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="12351-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="12351-141">Platforma özgü düzen ile struct.</span><span class="sxs-lookup"><span data-stu-id="12351-141">Struct with platform-specific layout.</span></span>|<span data-ttu-id="12351-142">Yerel paketleme tanımlarına sahip bir tür geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-142">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="12351-143">Platform örneği</span><span class="sxs-lookup"><span data-stu-id="12351-143">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="12351-144">Yapıda null değerler.</span><span class="sxs-lookup"><span data-stu-id="12351-144">Null values in structure.</span></span>|<span data-ttu-id="12351-145">Değer türüne başvuru yerine bir null başvurusu (Visual Basic**hiçbir şey** ) geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-145">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="12351-146">[HandleRef örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="12351-146">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="12351-147">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="12351-147">Structures sample</span></span>

<span data-ttu-id="12351-148">Bu örnek, ikinci yapıya işaret eden bir yapının nasıl geçirileceğini, gömülü bir yapıya sahip bir yapının nasıl geçirileceğini ve bir yapının gömülü dizi ile nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-148">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="12351-149">Yapılar örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="12351-149">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="12351-150">**Teststructsöylemek** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-150">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="12351-151">**TestStructInStruct3** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-151">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="12351-152">**Testarraybildirmek** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-152">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="12351-153">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlevler ve dört yapı için uygulamalar içeren özel bir yönetilmeyen kitaplıktır: **MyPerson**, **MyPerson2**, **MyPerson3**ve **MyArrayStruct**.</span><span class="sxs-lookup"><span data-stu-id="12351-153">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="12351-154">Bu yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="12351-154">These structures contain the following elements:</span></span>

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

<span data-ttu-id="12351-155">Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`ve `MyArrayStruct` yapıları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="12351-155">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="12351-156">`MyPerson`yalnızca dize üyelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-156">`MyPerson` contains only string members.</span></span> <span data-ttu-id="12351-157">[Karakter kümesi](specifying-a-character-set.md) alanı yönetilmeyen işleve GEÇIRILDIĞINDE dizeleri ANSI biçimine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12351-157">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="12351-158">`MyPerson2``MyPerson` yapıya bir **IntPtr** içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-158">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="12351-159">.NET Framework uygulamalar, kod **güvensiz**olarak işaretlenmedikçe işaretçileri kullanmadığı Için, **IntPtr** türü özgün işaretçinin yönetilmeyen yapıya göre yerini alır.</span><span class="sxs-lookup"><span data-stu-id="12351-159">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="12351-160">`MyPerson3`gömülü `MyPerson` yapı olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-160">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="12351-161">Başka bir yapıda gömülü bir yapı, gömülü yapının öğeleri doğrudan ana yapıya girilerek düzleştirilir veya bu örnekte yapıldığı gibi gömülü bir yapı olarak bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="12351-161">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="12351-162">`MyArrayStruct`bir tamsayılar dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-162">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="12351-163"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği, <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini dizideki öğelerin sayısını göstermek için kullanılan **ByValArray**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12351-163">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="12351-164">Bu örnekteki tüm yapılar için, üyelerin bellekte <xref:System.Runtime.InteropServices.StructLayoutAttribute> sırayla, göründükleri sırada düzenlendiğinden emin olmak için özniteliği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="12351-164">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="12351-165">`NativeMethods` Sınıfı `TestStructInStruct`, `TestStructInStruct3`, ve `TestArrayInStruct` `App` sınıfı tarafından çağrılan yöntemler için yönetilen prototürler içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-165">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="12351-166">Her prototip, aşağıdaki gibi tek bir parametre bildirir:</span><span class="sxs-lookup"><span data-stu-id="12351-166">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="12351-167">`TestStructInStruct`parametresi olarak yazmak `MyPerson2` için bir başvuru bildirir.</span><span class="sxs-lookup"><span data-stu-id="12351-167">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="12351-168">`TestStructInStruct3`türü `MyPerson3` parametresi olarak bildirir ve parametreyi değere göre geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-168">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="12351-169">`TestArrayInStruct`parametresi olarak yazmak `MyArrayStruct` için bir başvuru bildirir.</span><span class="sxs-lookup"><span data-stu-id="12351-169">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="12351-170">Parametreler **ref** (Visual Basic içinde**ByRef** ) anahtar sözcüğü içermiyorsa, yöntemlere bağımsız değişken olarak geçirilen yapılar değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="12351-170">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="12351-171">Örneğin, `TestStructInStruct` yöntemi bir başvurusu (bir adresin değeri) türünde `MyPerson2` bir nesneye, yönetilmeyen koda geçirir.</span><span class="sxs-lookup"><span data-stu-id="12351-171">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="12351-172">' A işaret eden `MyPerson2` yapıyı değiştirmek için örnek, belirtilen boyutun bir arabelleğini oluşturur ve <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemlerini birleştirerek adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="12351-172">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="12351-173">Ardından örnek, yönetilen yapının içeriğini yönetilmeyen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="12351-173">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="12351-174">Son olarak, örnek, yönetilmeyen <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> arabellekteki verileri yönetilen bir nesneye ve yönetilmeyen bellek bloğunu serbest bırakma <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yöntemine göre sıralamak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12351-174">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="12351-175">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="12351-175">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="12351-176">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="12351-176">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="12351-177">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="12351-177">FindFile sample</span></span>

<span data-ttu-id="12351-178">Bu örnek, yönetilmeyen bir işleve ikinci, gömülü bir yapı içeren bir yapının nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-178">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="12351-179">Ayrıca, yapı içinde sabit uzunluklu bir <xref:System.Runtime.InteropServices.MarshalAsAttribute> dizi bildirmek için özniteliği nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-179">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="12351-180">Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir.</span><span class="sxs-lookup"><span data-stu-id="12351-180">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="12351-181">Düzleştirilmemiş gömülü bir yapının örneği için bkz. [yapılar örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="12351-181">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="12351-182">FindFile örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="12351-182">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="12351-183">Kernel32. dll dosyasından bir **FindFirstFile** verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-183">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="12351-184">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="12351-184">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="12351-185">Bu örnekte, `FindData` sınıfı özgün yapıdaki her öğe için karşılık gelen bir veri üyesini ve katıştırılmış yapıyı içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-185">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="12351-186">İki orijinal karakter arabelleği yerine, sınıf yerine dizeler koyar.</span><span class="sxs-lookup"><span data-stu-id="12351-186">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="12351-187">**MarshalAsAttribute** <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmayı, yönetilmeyen yapılar içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek için kullanılan **ByValTStr**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="12351-187">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="12351-188">`NativeMethods` Sınıfı, `FindData` sınıfının bir parametre olarak geçişini sağlayan, yönetilen bir prototipi `FindFirstFile` içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-188">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="12351-189">Parametre, <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleri ile bildirilmelidir çünkü başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="12351-189">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="12351-190">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="12351-190">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="12351-191">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="12351-191">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="12351-192">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="12351-192">Unions sample</span></span>

<span data-ttu-id="12351-193">Bu örnek, yalnızca değer türlerini içeren yapıların ve bir değer türü içeren yapıların ve bir birleşim bekleyen yönetilmeyen bir işleve parametre olarak dize olarak nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-193">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="12351-194">Birleşim, iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12351-194">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="12351-195">Birleşimler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="12351-195">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="12351-196">**TestUnion** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-196">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="12351-197">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlev için bir uygulama ve **MyUnion** ve **MYUNION2**olmak üzere iki birleşim içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="12351-197">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="12351-198">Birleşimler aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="12351-198">The unions contain the following elements:</span></span>

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

<span data-ttu-id="12351-199">Yönetilen kodda birleşimler yapılar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="12351-199">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="12351-200">Yapı `MyUnion` , üyeleri olarak iki değer türü içerir: tamsayı ve çift.</span><span class="sxs-lookup"><span data-stu-id="12351-200">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="12351-201"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği her bir veri üyesinin kesin konumunu denetlemek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12351-201">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="12351-202"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Özniteliği, bir birleşimin yönetilmeyen gösterimi içindeki alanların fiziksel konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="12351-202">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="12351-203">Her iki üyenin de aynı fark değerlerine sahip olduğuna dikkat edin, bu nedenle Üyeler aynı bellek parçasını tanımlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="12351-203">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="12351-204">`MyUnion2_1`ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-204">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="12351-205">Yönetilen kodda, değer türleri ve başvuru türlerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="12351-205">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="12351-206">Bu örnek, çağıranın aynı yönetilmeyen işlevi çağırırken her iki türü de kullanmasını sağlamak için yöntem aşırı yüklemesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12351-206">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="12351-207">Düzeni `MyUnion2_1` açıktır ve kesin bir fark değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-207">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="12351-208">Buna karşılık, `MyUnion2_2` başvuru türlerinde açık mizanpajlara izin verilmediğinden sıralı bir düzene sahiptir.</span><span class="sxs-lookup"><span data-stu-id="12351-208">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="12351-209"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Özniteliği, UNION 'nin <xref:System.Runtime.InteropServices.UnmanagedType> yönetilmeyen gösterimi içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek için kullanılan **ByValTStr**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12351-209">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="12351-210">`NativeMethods` Sınıfı `TestUnion` ve `TestUnion2` yöntemlerinin prototiplerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-210">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="12351-211">`TestUnion2`, parametreleri bildirmek `MyUnion2_1` `MyUnion2_2` için aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="12351-211">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="12351-212">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="12351-212">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="12351-213">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="12351-213">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="12351-214">Platform örneği</span><span class="sxs-lookup"><span data-stu-id="12351-214">Platform sample</span></span>

<span data-ttu-id="12351-215">Bazı senaryolarda `struct` ve `union` düzenler hedeflenen platforma bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="12351-215">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="12351-216">Örneğin, bir COM senaryosunda [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) tanımlandığı zaman türü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="12351-216">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

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

<span data-ttu-id="12351-217">Yukarıdaki `struct` , türün bellek yerleşimini etkileyen Windows üstbilgileri ile bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="12351-217">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="12351-218">Yönetilen bir ortamda tanımlandığında, yerel kodla düzgün şekilde birlikte çalışmak için bu düzen ayrıntılarının olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="12351-218">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="12351-219">Bu türün 32 bitlik bir işlemde doğru yönetilen tanımı:</span><span class="sxs-lookup"><span data-stu-id="12351-219">The correct managed definition of this type in a 32-bit process is:</span></span>

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

<span data-ttu-id="12351-220">64 bit süreçte boyut *ve* alan uzaklıkları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="12351-220">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="12351-221">Doğru düzen:</span><span class="sxs-lookup"><span data-stu-id="12351-221">The correct layout is:</span></span>

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

<span data-ttu-id="12351-222">Bir birlikte çalışma senaryosunda yerel düzeni doğru şekilde düşünmeyen hata rastgele kilitlenmeler veya daha kötü hesaplamalar, yanlış hesaplamalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="12351-222">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="12351-223">Varsayılan olarak, .NET derlemeleri .NET çalışma zamanının 32-bit ve 64 bit sürümünde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="12351-223">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="12351-224">Uygulamanın, önceki tanımlardan hangisinin kullanılacağına karar vermek için çalışma zamanına kadar beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="12351-224">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="12351-225">Aşağıdaki kod parçacığı, çalışma zamanında 32-bit ve 64 bit tanım arasında nasıl seçim yapılacağı hakkında bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-225">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
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

## <a name="systime-sample"></a><span data-ttu-id="12351-226">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="12351-226">SysTime sample</span></span>

<span data-ttu-id="12351-227">Bu örnek, bir sınıfa işaretçi bekleyen yönetilmeyen bir işleve bir işaretçinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-227">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="12351-228">SysTime örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="12351-228">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="12351-229">Kernel32. dll ' den bir **GetSystemTime** verildi.</span><span class="sxs-lookup"><span data-stu-id="12351-229">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="12351-230">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="12351-230">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="12351-231">Bu örnekte, `SystemTime` sınıfı sınıf üyeleri olarak temsil edilen orijinal yapının öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-231">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="12351-232"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12351-232">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="12351-233">`NativeMethods` Sınıfı, varsayılan olarak `SystemTime` sınıfı bir ın/out parametresi olarak ileten `GetSystemTime` yönteminin yönetilen bir prototipini içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-233">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="12351-234">Parametre, <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleri ile bildirilmelidir çünkü başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="12351-234">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="12351-235">Çağıranın sonuçları alması için, bu [yönlü özniteliklerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="12351-235">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="12351-236">`App` Sınıfı, `SystemTime` sınıfının yeni bir örneğini oluşturur ve veri alanlarına erişir.</span><span class="sxs-lookup"><span data-stu-id="12351-236">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="12351-237">Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="12351-237">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="12351-238">OutArrayOfStructs örneği</span><span class="sxs-lookup"><span data-stu-id="12351-238">OutArrayOfStructs sample</span></span>

<span data-ttu-id="12351-239">Bu örnek, yönetilmeyen bir işleve tamsayı ve dizeler içeren bir yapı dizisinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-239">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="12351-240">Bu örnek, <xref:System.Runtime.InteropServices.Marshal> sınıfını kullanarak ve güvenli olmayan kod kullanarak yerel bir işlevin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12351-240">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="12351-241">Bu örnek, bir sarmalayıcı işlevleri ve kaynak dosyalarında da sağlanmış olan [PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll)içinde tanımlanan platform çağırır kullanır.</span><span class="sxs-lookup"><span data-stu-id="12351-241">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="12351-242">`TestOutArrayOfStructs` İşlevi ve `MYSTRSTRUCT2` yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="12351-242">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="12351-243">Yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="12351-243">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="12351-244">Sınıf `MyStruct` , ANSI karakterlerinden oluşan bir dize nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-244">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="12351-245"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Alan ANSI biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12351-245">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="12351-246">`MyUnsafeStruct`, bir dize yerine <xref:System.IntPtr> tür içeren bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="12351-246">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="12351-247">`NativeMethods` Sınıfı, aşırı yüklenmiş `TestOutArrayOfStructs` prototip metodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="12351-247">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="12351-248">Bir yöntem parametre olarak bir işaretçi bildirirse, sınıf `unsafe` anahtar sözcüğüyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="12351-248">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="12351-249">Visual Basic güvenli olmayan kod kullanamadığından, aşırı yüklenmiş yöntem, güvensiz değiştirici ve `MyUnsafeStruct` yapı gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="12351-249">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="12351-250">`App` Sınıfı, diziyi iletmek `UsingMarshaling` için gereken tüm görevleri gerçekleştiren yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="12351-250">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="12351-251">Dizi `out` (`ByRef` Visual Basic) anahtar sözcüğüyle işaretlenir ve bu, verilerin çağrıdan çağırana 'e geçtiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="12351-251">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="12351-252">Uygulama aşağıdaki <xref:System.Runtime.InteropServices.Marshal> sınıf yöntemlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="12351-252">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="12351-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>yönetilmeyen arabellekteki verileri yönetilen bir nesneye sıralama.</span><span class="sxs-lookup"><span data-stu-id="12351-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="12351-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>yapıdaki dizeler için ayrılan belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="12351-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="12351-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>dizi için ayrılan belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="12351-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="12351-256">Daha önce belirtildiği gibi, C# güvenli olmayan koda Izin veriyor ve Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="12351-256">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="12351-257">C# örneğinde, `UsingUnsafePointer` <xref:System.Runtime.InteropServices.Marshal> `MyUnsafeStruct` yapıyı içeren diziyi geri geçirmek için sınıfı yerine işaretçiler kullanan alternatif bir yöntem uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="12351-257">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="12351-258">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="12351-258">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="12351-259">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="12351-259">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="12351-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12351-260">See also</span></span>

- [<span data-ttu-id="12351-261">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="12351-261">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="12351-262">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="12351-262">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="12351-263">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="12351-263">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
