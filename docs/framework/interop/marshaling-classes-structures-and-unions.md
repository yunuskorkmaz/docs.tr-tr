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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c481b6889c1f10124465a4e851adfb25a1ba2eff
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890299"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="bff19-102">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="bff19-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="bff19-103">.NET Framework sınıfları ve yapıları benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bff19-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="bff19-104">Hem alanlar, özellikler ve olaylar olabilir.</span><span class="sxs-lookup"><span data-stu-id="bff19-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="bff19-105">Bunlar, ayrıca statik ve statik olmayan yöntemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="bff19-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="bff19-106">Bir önemli fark, yapılar değer türüdür ve sınıflar, başvuru türleridir ' dir.</span><span class="sxs-lookup"><span data-stu-id="bff19-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="bff19-107">Aşağıdaki tabloda, sınıflar, yapılar ve birleşimleri hazırlama seçenekleri listeler. bunların kullanımını açıklar; ve gelen platformun sayfaya bağlantı verilmektedir örnek çağırır.</span><span class="sxs-lookup"><span data-stu-id="bff19-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="bff19-108">Tür</span><span class="sxs-lookup"><span data-stu-id="bff19-108">Type</span></span>|<span data-ttu-id="bff19-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bff19-109">Description</span></span>|<span data-ttu-id="bff19-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="bff19-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="bff19-111">Değere göre sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bff19-111">Class by value.</span></span>|<span data-ttu-id="bff19-112">Tamsayı üyesi olan bir sınıf, yönetilen durumu gibi bir ın/Out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="bff19-113">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-113">SysTime sample</span></span>|  
|<span data-ttu-id="bff19-114">Değer yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-114">Structure by value.</span></span>|<span data-ttu-id="bff19-115">Parametreleri olduğu gibi yapıları geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="bff19-116">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-116">Structures sample</span></span>|  
|<span data-ttu-id="bff19-117">Başvuruya göre yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-117">Structure by reference.</span></span>|<span data-ttu-id="bff19-118">Yapıları In/Out parametresi geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="bff19-119">OSInfo örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-119">OSInfo sample</span></span>|  
|<span data-ttu-id="bff19-120">Yapı ile iç içe geçmiş yapılar (düzleştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="bff19-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="bff19-121">Yönetilmeyen işlev içinde iç içe geçmiş yapılar yapısıyla temsil eden bir sınıf geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="bff19-122">Yapısı için büyük bir yönetilen prototip yapısında düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bff19-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="bff19-123">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-123">FindFile sample</span></span>|  
|<span data-ttu-id="bff19-124">Başka bir yapıya bir işaretçi ile yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="bff19-125">Bir üye olarak ikinci bir yapıya bir işaretçi içeren yapısı geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="bff19-126">Yapılar Örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-126">Structures Sample</span></span>|  
|<span data-ttu-id="bff19-127">Tamsayı değeriyle yapılarıyla dizisi.</span><span class="sxs-lookup"><span data-stu-id="bff19-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="bff19-128">Bir dizi yalnızca tamsayı içeren bir ın/Out parametresi olarak yapılarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="bff19-129">Dizi üyelerinin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bff19-129">Members of the array can be changed.</span></span>|<span data-ttu-id="bff19-130">Diziler Örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-130">Arrays Sample</span></span>|  
|<span data-ttu-id="bff19-131">Tam sayılar ve dizeler başvuruya göre yapılarıyla dizisi.</span><span class="sxs-lookup"><span data-stu-id="bff19-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="bff19-132">Bir dizi tamsayılar ve dizelerin bir Out parametresi içeren yapılarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="bff19-133">Çağrılan işlev dizi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="bff19-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="bff19-134">OutArrayOfStructs Örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="bff19-135">Birleşimler ile değer türleri.</span><span class="sxs-lookup"><span data-stu-id="bff19-135">Unions with value types.</span></span>|<span data-ttu-id="bff19-136">Değer türleri (Integer ve double) ile birleşimler geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="bff19-137">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-137">Unions sample</span></span>|  
|<span data-ttu-id="bff19-138">Birleşimler karma türlerine sahip.</span><span class="sxs-lookup"><span data-stu-id="bff19-138">Unions with mixed types.</span></span>|<span data-ttu-id="bff19-139">Birleşimler (tamsayı ve dize) karma türleriyle geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="bff19-140">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-140">Unions sample</span></span>|  
|<span data-ttu-id="bff19-141">Null değerler yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-141">Null values in structure.</span></span>|<span data-ttu-id="bff19-142">Null bir başvuru geçirir (**hiçbir şey** Visual Basic'te) yerine bir değer türü referansı.</span><span class="sxs-lookup"><span data-stu-id="bff19-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="bff19-143">HandleRef örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="bff19-144">Yapılar örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-144">Structures sample</span></span>  
 <span data-ttu-id="bff19-145">Bu örnek, ikinci bir yapısına işaret eden bir yapı geçirmek, katıştırılmış bir yapıya sahip bir yapı geçirin ve bir gömülü dizi yapısıyla geçirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff19-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="bff19-146">Yapılar örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="bff19-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="bff19-147">**TestStructInStruct** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="bff19-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="bff19-148">**TestStructInStruct3** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="bff19-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="bff19-149">**TestArrayInStruct** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="bff19-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="bff19-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) uygulamaları için daha önce listelenen işlevlerin ve dört yapıları içeren özel bir yönetilmeyen kitaplıktır: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, ve **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="bff19-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="bff19-151">Bu yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bff19-151">These structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="bff19-152">Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`, ve `MyArrayStruct` yapılar aşağıdaki özellik vardır:</span><span class="sxs-lookup"><span data-stu-id="bff19-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   `MyPerson` <span data-ttu-id="bff19-153">yalnızca dize üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bff19-153">contains only string members.</span></span> <span data-ttu-id="bff19-154">[CharSet](specifying-a-character-set.md) alan yönetilmeyen işleve geçirildiğinde ANSI biçim dizeleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bff19-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   `MyPerson2` <span data-ttu-id="bff19-155">içeren bir **IntPtr** için `MyPerson` yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-155">contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="bff19-156">**IntPtr** türü .NET Framework uygulamaları kod işaretlenmediği sürece işaretçileri kullanmadığından yönetilmeyen yapısına orijinal işaretçiyle değiştirir **güvenli**.</span><span class="sxs-lookup"><span data-stu-id="bff19-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   `MyPerson3` <span data-ttu-id="bff19-157">içeren `MyPerson` katıştırılmış bir yapı olarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-157">contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="bff19-158">Başka bir yapı içinde katıştırılmış bir yapı ana yapısına doğrudan katıştırılmış yapısı öğelerini yerleştirerek düzleştirilebilir veya katıştırılmış bir yapısı olarak, bu örnekte olduğu gibi bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="bff19-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   `MyArrayStruct` <span data-ttu-id="bff19-159">tamsayı dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="bff19-159">contains an array of integers.</span></span> <span data-ttu-id="bff19-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümeleri <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değerini **ByValArray**, dizideki öğelerin sayısını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bff19-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="bff19-161">Bu örnekte, tüm yapıları için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bff19-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="bff19-162">`LibWrap` Sınıfı için yönetilen prototipleri içeren `TestStructInStruct`, `TestStructInStruct3`, ve `TestArrayInStruct` çağıran yöntemleri `App` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bff19-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="bff19-163">Her bir prototip gibi tek bir parametre bildirir:</span><span class="sxs-lookup"><span data-stu-id="bff19-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   `TestStructInStruct` <span data-ttu-id="bff19-164">bir başvuru türüne bildirir `MyPerson2` parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-164">declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   `TestStructInStruct3` <span data-ttu-id="bff19-165">tür bildirir `MyPerson3` parametre olarak ve parametre değeri geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-165">declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   `TestArrayInStruct` <span data-ttu-id="bff19-166">bir başvuru türüne bildirir `MyArrayStruct` parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-166">declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="bff19-167">Parametre içermedikçe yöntemlerinin bağımsız değişkenleri değere göre geçirilir gibi yapıları **ref** (**ByRef** Visual Basic'te) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bff19-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="bff19-168">Örneğin, `TestStructInStruct` yöntemi (bir adresi değeri) başvuru türünde bir nesne geçirir `MyPerson2` yönetilmeyen kod için.</span><span class="sxs-lookup"><span data-stu-id="bff19-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="bff19-169">Yapıyı işlemek için `MyPerson2` noktaları için örnek bir arabellek belirli bir boyuttaki oluşturur ve birleştirerek adresini döndürür <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bff19-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bff19-170">Ardından, örnek içerik yönetilen yapısı yönetilmeyen arabelleğe kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bff19-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="bff19-171">Son olarak, örnek kullanır <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> sıralama verilerini bir yönteme bir yönetilen nesneye yönetilmeyen arabellekteki ve <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yönetilmeyen bellek bloğunu serbest bırakmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bff19-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="bff19-172">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="bff19-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="bff19-173">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="bff19-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="bff19-174">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-174">FindFile sample</span></span>  
 <span data-ttu-id="bff19-175">Bu örnek yönetilmeyen bir işleve ikinci, katıştırılmış bir yapı içeren bir yapının nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff19-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="bff19-176">Ayrıca nasıl kullanılacağını gösterir <xref:System.Runtime.InteropServices.MarshalAsAttribute> yapısı içinde bir sabit uzunluklu diziyi bildirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bff19-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="bff19-177">Bu örnekte, katıştırılmış yapı öğeleri üst yapıya eklenir.</span><span class="sxs-lookup"><span data-stu-id="bff19-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="bff19-178">Değil düzleştirilmiş katıştırılmış bir yapının bir örnek için bkz [yapılar örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bff19-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>  
  
 <span data-ttu-id="bff19-179">FindFile örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="bff19-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="bff19-180">**FindFirstFile** Kernel32.dll öğesinden dışa aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bff19-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="bff19-181">İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bff19-181">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="bff19-182">Bu örnekte `FindData` orijinal yapı ve katıştırılmış yapısı her öğesi için karşılık gelen bir veri üyesi sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="bff19-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="bff19-183">İki orijinal karakter arabelleği yerine sınıfı, dizeleri yerini alır.</span><span class="sxs-lookup"><span data-stu-id="bff19-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="bff19-184">**MarshalAsAttribute** ayarlar <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesine **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunluklu karakteri diziler yönetilmeyen yapıları içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="bff19-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="bff19-185">`LibWrap` Sınıfı içeren yönetilen bir prototipi `FindFirstFile` geçirir yöntemi `FindData` bir parametre olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="bff19-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="bff19-186">Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreler geçirildiğinden öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="bff19-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="bff19-187">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="bff19-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="bff19-188">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="bff19-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="bff19-189">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-189">Unions sample</span></span>  
 <span data-ttu-id="bff19-190">Bu örnek yalnızca değer türleri içeren yapılara ve bir birleşim bekleniyor yönetilmeyen bir işlev için parametre olarak bir değer türü ve bir dize içeren yapıları nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff19-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="bff19-191">UNION iki veya daha fazla değişken tarafından paylaşılabilen bir bellek konumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bff19-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="bff19-192">Birleşimler örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="bff19-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="bff19-193">**TestUnion** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="bff19-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="bff19-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) daha önce listelenen işlev ve iki birleşimler için bir uygulama içeren özel bir yönetilmeyen kitaplıktır **MYUNION** ve **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="bff19-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="bff19-195">Birleşimler aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bff19-195">The unions contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="bff19-196">Yönetilen kodda birleşimler yapı olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bff19-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="bff19-197">`MyUnion` Yapı üyeleri olarak iki değer türleri içeriyor: tamsayı ve bir çift.</span><span class="sxs-lookup"><span data-stu-id="bff19-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="bff19-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, her veri üyesi kesin konumunu denetlemek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bff19-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="bff19-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Özniteliği, yönetilmeyen temsili bir birleşim alanlarını fiziksel konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="bff19-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="bff19-200">Üyeleri aynı parça bellek bu sayede her iki üye aynı uzaklık değerleri sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="bff19-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 `MyUnion2_1` <span data-ttu-id="bff19-201">ve `MyUnion2_2` bir değer türü (tamsayı) ve bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="bff19-201">and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="bff19-202">Yönetilen kodda değer türleri ve başvuru türleri çakıştırmayı izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="bff19-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="bff19-203">Bu örnek iki türü de aynı yönetilmeyen işlev çağrılırken kullanılacak çağıran etkinleştirmek için aşırı yükleme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bff19-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="bff19-204">Düzenini `MyUnion2_1` açık olduğunu ve kesin bir uzaklık değeri.</span><span class="sxs-lookup"><span data-stu-id="bff19-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="bff19-205">Buna karşılık, `MyUnion2_2` açık düzenleri başvuru türleri için verilmeyen bir ardışık düzen sahip.</span><span class="sxs-lookup"><span data-stu-id="bff19-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="bff19-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümeleri <xref:System.Runtime.InteropServices.UnmanagedType> sabit listesine **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunluklu karakteri diziler yönetilmeyen gösterimini Birliği içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="bff19-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="bff19-207">`LibWrap` Sınıfı içeren yönelik prototipleri `TestUnion` ve `TestUnion2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bff19-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> `TestUnion2` <span data-ttu-id="bff19-208">bildirmek için aşırı yüklenmiş `MyUnion2_1` veya `MyUnion2_2` parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-208">is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="bff19-209">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="bff19-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="bff19-210">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="bff19-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="bff19-211">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-211">SysTime sample</span></span>  
 <span data-ttu-id="bff19-212">Bu örnek, bir sınıf bir yapıya bir işaretçi bekliyor yönetilmeyen bir işleve işaretçi nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff19-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="bff19-213">SysTime örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="bff19-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="bff19-214">**GetSystemTime** Kernel32.dll öğesinden dışa aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bff19-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="bff19-215">İşleve geçirilen orijinal yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bff19-215">The original structure passed to the function contains the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="bff19-216">Bu örnekte `SystemTime` sınıfı özgün yapısının sınıfı üyeleri olarak temsil edilen öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bff19-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="bff19-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bff19-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="bff19-218">`LibWrap` Sınıfı içeren yönetilen bir prototipi `GetSystemTime` geçirir yöntemi `SystemTime` sınıfı olarak bir ın/Out parametresinin varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="bff19-219">Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreler geçirildiğinden öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="bff19-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="bff19-220">Sonuçları almak çağırıcı için bunlar [yönlü öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) açıkça uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bff19-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="bff19-221">`App` Sınıfının yeni bir örneğini oluşturur `SystemTime` sınıfı ve veri alanlarını erişir.</span><span class="sxs-lookup"><span data-stu-id="bff19-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="bff19-222">Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="bff19-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="bff19-223">OutArrayOfStructs örneği</span><span class="sxs-lookup"><span data-stu-id="bff19-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="bff19-224">Bu örnek, tamsayı ve dış parametrelerin yönetilmeyen bir işlev için dize olarak içeren bir dizi yapıların nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff19-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="bff19-225">Bu örnek kullanarak yerel bir işlev çağırmayı göstermektedir <xref:System.Runtime.InteropServices.Marshal> sınıfı ve güvenli olmayan kod kullanarak.</span><span class="sxs-lookup"><span data-stu-id="bff19-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="bff19-226">Bu örnek bir sarmalayıcı işlevleri kullanır ve platform çağırır tanımlanan [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), da sağlanan kaynak dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="bff19-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="bff19-227">Kullandığı `TestOutArrayOfStructs` işlevi ve `MYSTRSTRUCT2` yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="bff19-228">Yapı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bff19-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="bff19-229">`MyStruct` Sınıfı içeren bir dize nesnesi ANSI karakter.</span><span class="sxs-lookup"><span data-stu-id="bff19-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="bff19-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Alanı ANSI biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bff19-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> `MyUnsafeStruct`<span data-ttu-id="bff19-231">, bir yapı olduğunu içeren bir <xref:System.IntPtr> türü bir dize yerine.</span><span class="sxs-lookup"><span data-stu-id="bff19-231">, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="bff19-232">`LibWrap` Sınıfı içeren Aşırı yüklenen `TestOutArrayOfStructs` prototip yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bff19-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="bff19-233">İle bir yöntem parametresi olarak bir işaretçiyi bildirir, sınıf işaretlenmelidir `unsafe` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bff19-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="bff19-234">Çünkü [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] güvenli olmayan kod, aşırı yüklenmiş yöntemin güvenli olmayan değiştirici kullanamazsınız ve `MyUnsafeStruct` yapısı gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="bff19-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="bff19-235">`App` Sınıfının Implements `UsingMarshaling` dizi geçirmek için gerekli tüm görevleri gerçekleştiren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bff19-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="bff19-236">Dizi ile işaretlenmiş `out` (`ByRef` Visual Basic'te) verileri göstermek için anahtar sözcüğü, çağırana çağrılan geçirir.</span><span class="sxs-lookup"><span data-stu-id="bff19-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="bff19-237">Aşağıdaki uygulama kullanan <xref:System.Runtime.InteropServices.Marshal> sınıfı yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="bff19-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> <span data-ttu-id="bff19-238">yönetilen bir nesnenin yönetilmeyen buffer'dan alınan verileri hazırlamak için.</span><span class="sxs-lookup"><span data-stu-id="bff19-238">to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> <span data-ttu-id="bff19-239">yapısında dizeler için ayrılan belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="bff19-239">to release the memory reserved for strings in the structure.</span></span>  
  
-   <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> <span data-ttu-id="bff19-240">dizi için ayrılmış belleği serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="bff19-240">to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="bff19-241">Daha önce belirtildiği gibi C# güvenli olmayan koda izin verir ve [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bff19-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="bff19-242">İçinde C# örneği `UsingUnsafePointer` işaretçileri yerine kullanan alternatif bir yöntem uygulamasıdır <xref:System.Runtime.InteropServices.Marshal> geçirmek için sınıfı yeniden diziyi içeren `MyUnsafeStruct` yapısı.</span><span class="sxs-lookup"><span data-stu-id="bff19-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="bff19-243">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="bff19-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="bff19-244">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="bff19-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="bff19-245">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bff19-245">See also</span></span>
- [<span data-ttu-id="bff19-246">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="bff19-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="bff19-247">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="bff19-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="bff19-248">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="bff19-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
