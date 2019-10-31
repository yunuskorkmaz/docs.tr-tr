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
ms.openlocfilehash: 669e147f9c7b4ba901ade38f1ab8b41163c4f125
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114021"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="4ce9d-102">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4ce9d-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="4ce9d-103">Sınıflar ve yapılar .NET Framework benzerdir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="4ce9d-104">Her ikisinde de alanlar, Özellikler ve olaylar olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="4ce9d-105">Statik ve statik olmayan yöntemlere de sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="4ce9d-106">Bir önemli farkı, yapıların değer türleri ve sınıfların başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="4ce9d-107">Aşağıdaki tablo sınıflar, yapılar ve birleşimler için sıralama seçeneklerini listeler; kullanımlarını açıklar; ve buna karşılık gelen platform çağırma örneğine bir bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="4ce9d-108">Tür</span><span class="sxs-lookup"><span data-stu-id="4ce9d-108">Type</span></span>|<span data-ttu-id="4ce9d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ce9d-109">Description</span></span>|<span data-ttu-id="4ce9d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ce9d-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="4ce9d-111">Değere göre sınıf.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-111">Class by value.</span></span>|<span data-ttu-id="4ce9d-112">Tamsayı üyeleri olan bir sınıfı, yönetilen durum gibi bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="4ce9d-113">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-113">SysTime sample</span></span>|  
|<span data-ttu-id="4ce9d-114">Değere göre yapı.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-114">Structure by value.</span></span>|<span data-ttu-id="4ce9d-115">Yapıları parametrelerde olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="4ce9d-116">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-116">Structures sample</span></span>|  
|<span data-ttu-id="4ce9d-117">Başvuruya göre yapı.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-117">Structure by reference.</span></span>|<span data-ttu-id="4ce9d-118">Yapıları ın/out parametreleri olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="4ce9d-119">OSInfo örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-119">OSInfo sample</span></span>|  
|<span data-ttu-id="4ce9d-120">İç içe yapılar (düzleştirilmiş) ile yapı.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="4ce9d-121">Yönetilmeyen işlevde iç içe yapılar içeren bir yapıyı temsil eden bir sınıf geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="4ce9d-122">Yapı, yönetilen prototipde bir büyük yapıya düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="4ce9d-123">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-123">FindFile sample</span></span>|  
|<span data-ttu-id="4ce9d-124">Başka bir yapıya işaretçi içeren yapı.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="4ce9d-125">İkinci bir yapıya bir işaretçi içeren bir yapıyı üye olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="4ce9d-126">Yapılar Örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-126">Structures Sample</span></span>|  
|<span data-ttu-id="4ce9d-127">Değere göre tamsayılar içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="4ce9d-128">Yalnızca tamsayı içeren bir yapı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="4ce9d-129">Dizi üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-129">Members of the array can be changed.</span></span>|<span data-ttu-id="4ce9d-130">Diziler Örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-130">Arrays Sample</span></span>|  
|<span data-ttu-id="4ce9d-131">Başvuruya göre tamsayılar ve dizeler içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="4ce9d-132">Out parametresi olarak tamsayılar ve dizeler içeren bir yapı dizisini geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="4ce9d-133">Çağrılan işlev dizi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="4ce9d-134">OutArrayOfStructs Örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="4ce9d-135">Değer türleri olan birleşimler.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-135">Unions with value types.</span></span>|<span data-ttu-id="4ce9d-136">Birleşimleri değer türleriyle geçirir (tamsayı ve çift).</span><span class="sxs-lookup"><span data-stu-id="4ce9d-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="4ce9d-137">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-137">Unions sample</span></span>|  
|<span data-ttu-id="4ce9d-138">Karışık Türler içeren birleşimler.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-138">Unions with mixed types.</span></span>|<span data-ttu-id="4ce9d-139">Birleşimleri karışık türler (tamsayı ve dize) ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="4ce9d-140">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-140">Unions sample</span></span>|  
|<span data-ttu-id="4ce9d-141">Yapıda null değerler.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-141">Null values in structure.</span></span>|<span data-ttu-id="4ce9d-142">Değer türüne başvuru yerine bir null başvurusu (Visual Basic**hiçbir şey** ) geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="4ce9d-143">HandleRef örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="4ce9d-144">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-144">Structures sample</span></span>  
 <span data-ttu-id="4ce9d-145">Bu örnek, ikinci yapıya işaret eden bir yapının nasıl geçirileceğini, gömülü bir yapıya sahip bir yapının nasıl geçirileceğini ve bir yapının gömülü dizi ile nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="4ce9d-146">Yapılar örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="4ce9d-147">**Teststructsöylemek** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- <span data-ttu-id="4ce9d-148">**TestStructInStruct3** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- <span data-ttu-id="4ce9d-149">**Testarraybildirmek** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="4ce9d-150">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlevler ve dört yapı için uygulamalar içeren özel bir yönetilmeyen kitaplıktır: **MyPerson**, **MyPerson2**, **MyPerson3**ve **MyArrayStruct**.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="4ce9d-151">Bu yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-151">These structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4ce9d-152">Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`ve `MyArrayStruct` yapıları aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
- <span data-ttu-id="4ce9d-153">`MyPerson` yalnızca dize üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="4ce9d-154">[Karakter kümesi](specifying-a-character-set.md) alanı yönetilmeyen işleve GEÇIRILDIĞINDE dizeleri ANSI biçimine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
- <span data-ttu-id="4ce9d-155">`MyPerson2`, `MyPerson` yapısına bir **IntPtr** içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="4ce9d-156">.NET Framework uygulamalar, kod **güvensiz**olarak işaretlenmedikçe işaretçileri kullanmadığı Için, **IntPtr** türü özgün işaretçinin yönetilmeyen yapıya göre yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
- <span data-ttu-id="4ce9d-157">`MyPerson3`, gömülü bir yapı olarak `MyPerson` içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="4ce9d-158">Başka bir yapıda gömülü bir yapı, gömülü yapının öğeleri doğrudan ana yapıya girilerek düzleştirilir veya bu örnekte yapıldığı gibi gömülü bir yapı olarak bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
- <span data-ttu-id="4ce9d-159">`MyArrayStruct` bir tamsayılar dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="4ce9d-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, dizideki öğelerin sayısını göstermek için kullanılan <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini **ByValArray**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="4ce9d-161">Bu örnekteki tüm yapılar için, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="4ce9d-162">`NativeMethods` sınıfı, `App` sınıfı tarafından çağrılan `TestStructInStruct`, `TestStructInStruct3`ve `TestArrayInStruct` yöntemleri için yönetilen prototürler içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-162">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="4ce9d-163">Her prototip, aşağıdaki gibi tek bir parametre bildirir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-163">Each prototype declares a single parameter, as follows:</span></span>  
  
- <span data-ttu-id="4ce9d-164">`TestStructInStruct`, parametresi olarak `MyPerson2` yazmak için bir başvuru bildirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
- <span data-ttu-id="4ce9d-165">`TestStructInStruct3`, parametre olarak `MyPerson3` türü bildirir ve parametreyi değere göre geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
- <span data-ttu-id="4ce9d-166">`TestArrayInStruct`, parametresi olarak `MyArrayStruct` yazmak için bir başvuru bildirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="4ce9d-167">Parametreler **ref** (Visual Basic içinde**ByRef** ) anahtar sözcüğü içermiyorsa, yöntemlere bağımsız değişken olarak geçirilen yapılar değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="4ce9d-168">Örneğin `TestStructInStruct` yöntemi, yönetilmeyen koda `MyPerson2` türünde bir nesneye bir başvuru (bir adres değeri) geçirir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="4ce9d-169">`MyPerson2`, işaret eden yapıyı değiştirmek için, örnek belirtilen boyutun bir arabelleğini oluşturur ve <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemlerini birleştirerek adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4ce9d-170">Ardından örnek, yönetilen yapının içeriğini yönetilmeyen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="4ce9d-171">Son olarak, örnek, yönetilmeyen arabellekteki verileri yönetilen bir nesneye ve yönetilmeyen bellek bloğunu serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yöntemine aktarmak üzere <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4ce9d-172">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="4ce9d-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4ce9d-173">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="4ce9d-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="4ce9d-174">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-174">FindFile sample</span></span>  
 <span data-ttu-id="4ce9d-175">Bu örnek, yönetilmeyen bir işleve ikinci, gömülü bir yapı içeren bir yapının nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="4ce9d-176">Ayrıca, yapı içinde sabit uzunluklu bir dizi bildirmek için <xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="4ce9d-177">Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="4ce9d-178">Düzleştirilmemiş gömülü bir yapının örneği için bkz. [yapılar örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4ce9d-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>  
  
 <span data-ttu-id="4ce9d-179">FindFile örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="4ce9d-180">Kernel32. dll dosyasından bir **FindFirstFile** verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="4ce9d-181">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-181">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4ce9d-182">Bu örnekte, `FindData` sınıfı özgün yapıdaki her öğe için karşılık gelen bir veri üyesini ve katıştırılmış yapıyı içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="4ce9d-183">İki orijinal karakter arabelleği yerine, sınıf yerine dizeler koyar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="4ce9d-184">**MarshalAsAttribute** <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmayı, yönetilmeyen yapılar içinde görünen satır içi, sabit uzunluklu karakter dizilerini belirlemek Için kullanılan **ByValTStr**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="4ce9d-185">`NativeMethods` sınıfı, `FindData` sınıfını bir parametre olarak geçiren `FindFirstFile` yönteminin yönetilen bir prototipini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-185">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="4ce9d-186">Parametre, başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirildiğinden <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleriyle bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4ce9d-187">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="4ce9d-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4ce9d-188">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="4ce9d-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="4ce9d-189">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-189">Unions sample</span></span>  
 <span data-ttu-id="4ce9d-190">Bu örnek, yalnızca değer türlerini içeren yapıların ve bir değer türü içeren yapıların ve bir birleşim bekleyen yönetilmeyen bir işleve parametre olarak dize olarak nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="4ce9d-191">Birleşim, iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="4ce9d-192">Birleşimler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="4ce9d-193">**TestUnion** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="4ce9d-194">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenmiş işlev için bir uygulama ve **MyUnion** ve **MYUNION2**olmak üzere iki birleşim içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="4ce9d-195">Birleşimler aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-195">The unions contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4ce9d-196">Yönetilen kodda birleşimler yapılar olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="4ce9d-197">`MyUnion` yapısı, üyeleri olarak iki değer türü içerir: tamsayı ve çift.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="4ce9d-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği her bir veri üyesinin kesin konumunu denetlemek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="4ce9d-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> özniteliği, bir birleşimin yönetilmeyen gösterimi içindeki alanların fiziksel konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="4ce9d-200">Her iki üyenin de aynı fark değerlerine sahip olduğuna dikkat edin, bu nedenle Üyeler aynı bellek parçasını tanımlayabilirler.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="4ce9d-201">`MyUnion2_1` ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="4ce9d-202">Yönetilen kodda, değer türleri ve başvuru türlerinin örtüşmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="4ce9d-203">Bu örnek, çağıranın aynı yönetilmeyen işlevi çağırırken her iki türü de kullanmasını sağlamak için yöntem aşırı yüklemesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="4ce9d-204">`MyUnion2_1` düzeni açıktır ve kesin bir fark değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="4ce9d-205">Buna karşılık, `MyUnion2_2` sıralı bir düzene sahiptir, çünkü açık düzenlerine başvuru türleriyle izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="4ce9d-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> özniteliği, birleşimin yönetilmeyen gösterimi içinde görünen satır içi, sabit uzunlukta karakter dizilerini belirlemek için kullanılan <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırmayı **ByValTStr**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="4ce9d-207">`NativeMethods` sınıfı, `TestUnion` ve `TestUnion2` yöntemlerinin prototiptürlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-207">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="4ce9d-208">`TestUnion2`, `MyUnion2_1` veya `MyUnion2_2` parametre olarak bildirmek için aşırı yüklendi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4ce9d-209">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="4ce9d-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4ce9d-210">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="4ce9d-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="4ce9d-211">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-211">SysTime sample</span></span>  
 <span data-ttu-id="4ce9d-212">Bu örnek, bir sınıfa işaretçi bekleyen yönetilmeyen bir işleve bir işaretçinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="4ce9d-213">SysTime örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="4ce9d-214">Kernel32. dll ' den bir **GetSystemTime** verildi.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="4ce9d-215">İşleve geçirilen özgün yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-215">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="4ce9d-216">Bu örnekte, `SystemTime` sınıfı sınıf üyeleri olarak temsil edilen orijinal yapının öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="4ce9d-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="4ce9d-218">`NativeMethods` sınıfı, varsayılan olarak `SystemTime` sınıfını bir ın/out parametresi olarak geçiren `GetSystemTime` yönteminin yönetilen bir prototipini içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-218">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="4ce9d-219">Parametre, başvuru türleri olan sınıflar varsayılan olarak parametrelerde olarak geçirildiğinden <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleriyle bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="4ce9d-220">Çağıranın sonuçları alması için, bu [yönlü özniteliklerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="4ce9d-221">`App` sınıfı, `SystemTime` sınıfının yeni bir örneğini oluşturur ve veri alanlarına erişir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="4ce9d-222">Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4ce9d-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="4ce9d-223">OutArrayOfStructs örneği</span><span class="sxs-lookup"><span data-stu-id="4ce9d-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="4ce9d-224">Bu örnek, yönetilmeyen bir işleve tamsayı ve dizeler içeren bir yapı dizisinin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="4ce9d-225">Bu örnek, <xref:System.Runtime.InteropServices.Marshal> sınıfını kullanarak ve güvenli olmayan kod kullanarak yerel bir işlevin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="4ce9d-226">Bu örnek, bir sarmalayıcı işlevleri ve kaynak dosyalarında da sağlanmış olan [PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll)içinde tanımlanan platform çağırır kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="4ce9d-227">`TestOutArrayOfStructs` işlevini ve `MYSTRSTRUCT2` yapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="4ce9d-228">Yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-228">The structure contains the following elements:</span></span>  
  
```cpp
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="4ce9d-229">`MyStruct` sınıfı, ANSI karakterlerinden oluşan bir dize nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="4ce9d-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> alanı ANSI biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="4ce9d-231">`MyUnsafeStruct`, bir dize yerine <xref:System.IntPtr> türü içeren bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="4ce9d-232">`NativeMethods` sınıfı, aşırı yüklenmiş `TestOutArrayOfStructs` prototip metodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-232">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="4ce9d-233">Bir yöntem parametre olarak bir işaretçi bildirirse, sınıf `unsafe` anahtar sözcüğüyle işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="4ce9d-234">Visual Basic güvenli olmayan kod kullanamadığından, aşırı yüklenmiş yöntem, güvensiz değiştirici ve `MyUnsafeStruct` yapısı gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-234">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="4ce9d-235">`App` sınıfı, diziyi iletmek için gereken tüm görevleri gerçekleştiren `UsingMarshaling` yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="4ce9d-236">Dizi, verilerin çağrıdan arayana geçerken`ByRef` `out` olduğunu göstermek için Visual Basic) anahtar sözcüğüyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="4ce9d-237">Uygulama aşağıdaki <xref:System.Runtime.InteropServices.Marshal> sınıf yöntemlerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ce9d-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
- <span data-ttu-id="4ce9d-238">yönetilmeyen arabellekteki verileri yönetilen bir nesneye sıralama <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
- <span data-ttu-id="4ce9d-239">yapıdaki dizeler için ayrılan belleği serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
- <span data-ttu-id="4ce9d-240">dizi için ayrılan belleği serbest bırakmak için <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="4ce9d-241">Daha önce belirtildiği gibi C# , güvenli olmayan koda izin verir ve Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-241">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="4ce9d-242">C# Örnekte `UsingUnsafePointer`, `MyUnsafeStruct` yapısını içeren diziyi geri geçirmek için <xref:System.Runtime.InteropServices.Marshal> sınıfı yerine işaretçiler kullanan alternatif bir yöntem uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="4ce9d-243">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="4ce9d-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="4ce9d-244">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="4ce9d-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4ce9d-245">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ce9d-245">See also</span></span>

- [<span data-ttu-id="4ce9d-246">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4ce9d-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="4ce9d-247">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4ce9d-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="4ce9d-248">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4ce9d-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
