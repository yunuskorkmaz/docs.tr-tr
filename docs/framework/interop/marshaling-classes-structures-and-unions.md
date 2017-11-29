---
title: "Sınıflar, Yapılar ve Birleşimleri Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dcfa2e60a9659db6d38e0561785ece5726989ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="8adcd-102">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="8adcd-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="8adcd-103">.NET Framework sınıfları ve yapıları benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="8adcd-104">Her ikisi de alanları, özellikleri ve olayları olabilir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="8adcd-105">Ayrıca statik ve statik olmayan yöntemleri sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="8adcd-106">Bir dikkat çekici fark yapıları değer türleri ve başvuru türleri sınıflardır olduğundan ' dir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="8adcd-107">Aşağıdaki tabloda, sınıflar, yapılar ve birleşimleri hazırlama seçeneklerini listeler. bunların kullanım açıklar; ve karşılık gelen platform için bir bağlantı sağlar örnek çağırma.</span><span class="sxs-lookup"><span data-stu-id="8adcd-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="8adcd-108">Tür</span><span class="sxs-lookup"><span data-stu-id="8adcd-108">Type</span></span>|<span data-ttu-id="8adcd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8adcd-109">Description</span></span>|<span data-ttu-id="8adcd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8adcd-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="8adcd-111">Sınıfı tarafından değeri.</span><span class="sxs-lookup"><span data-stu-id="8adcd-111">Class by value.</span></span>|<span data-ttu-id="8adcd-112">Yönetilen servis talebi gibi bir giriş/çıkış parametresi olarak bir sınıf tamsayı üyeleriyle geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="8adcd-113">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-113">SysTime sample</span></span>|  
|<span data-ttu-id="8adcd-114">Değere göre yapısı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-114">Structure by value.</span></span>|<span data-ttu-id="8adcd-115">Yapıları parametreleri olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="8adcd-116">Yapıları örnek</span><span class="sxs-lookup"><span data-stu-id="8adcd-116">Structures sample</span></span>|  
|<span data-ttu-id="8adcd-117">Başvuruya göre yapısı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-117">Structure by reference.</span></span>|<span data-ttu-id="8adcd-118">Yapıları olarak In/Out parametreleri geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="8adcd-119">OSInfo örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-119">OSInfo sample</span></span>|  
|<span data-ttu-id="8adcd-120">İç içe geçmiş yapılar (düzleştirilmiş) yapısıyla.</span><span class="sxs-lookup"><span data-stu-id="8adcd-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="8adcd-121">Yönetilmeyen işlevinde iç içe geçmiş yapılar yapısıyla temsil eden bir sınıf geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="8adcd-122">Yönetilen prototip bir büyük yapısına yapısı düzleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="8adcd-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="8adcd-123">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-123">FindFile sample</span></span>|  
|<span data-ttu-id="8adcd-124">Başka bir yapısına yönelik işaretçinin yapısıyla.</span><span class="sxs-lookup"><span data-stu-id="8adcd-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="8adcd-125">Bir üye olarak ikinci bir yapı için bir işaretçi içeren bir yapısı geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="8adcd-126">Yapılar Örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-126">Structures Sample</span></span>|  
|<span data-ttu-id="8adcd-127">Değere göre tamsayılı yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="8adcd-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="8adcd-128">Bir giriş/çıkış parametresi olarak yalnızca tamsayı içeren yapılarını dizisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="8adcd-129">Dizi üyelerinin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-129">Members of the array can be changed.</span></span>|<span data-ttu-id="8adcd-130">Diziler Örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-130">Arrays Sample</span></span>|  
|<span data-ttu-id="8adcd-131">Yapıları tamsayılar ve başvuruya göre dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="8adcd-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="8adcd-132">Tamsayıları ve dizeleri bir çıkış parametresi olarak içeren yapılarını dizisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="8adcd-133">Çağrılan işlev dizi için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="8adcd-134">OutArrayOfStructs Örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="8adcd-135">Değer türleri ile birleşimler.</span><span class="sxs-lookup"><span data-stu-id="8adcd-135">Unions with value types.</span></span>|<span data-ttu-id="8adcd-136">Değer türleri (tamsayı ve çift) ile birleşimler geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="8adcd-137">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-137">Unions sample</span></span>|  
|<span data-ttu-id="8adcd-138">Birleşimler karma türleriyle.</span><span class="sxs-lookup"><span data-stu-id="8adcd-138">Unions with mixed types.</span></span>|<span data-ttu-id="8adcd-139">Birleşimler (tamsayı ve dize) karma türleriyle geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="8adcd-140">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-140">Unions sample</span></span>|  
|<span data-ttu-id="8adcd-141">Null değerler yapısındaki.</span><span class="sxs-lookup"><span data-stu-id="8adcd-141">Null values in structure.</span></span>|<span data-ttu-id="8adcd-142">Bir null başvuru geçirir (**hiçbir şey** Visual Basic'te) yerine bir değer türü referansı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="8adcd-143">HandleRef örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="8adcd-144">Yapıları örnek</span><span class="sxs-lookup"><span data-stu-id="8adcd-144">Structures sample</span></span>  
 <span data-ttu-id="8adcd-145">Bu örnek, ikinci bir yapıya işaret eden bir yapı geçirmek için bir katıştırılmış yapısı yapısıyla geçip katıştırılmış bir dizi yapısıyla geçirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="8adcd-146">Yapılar örnek kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="8adcd-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="8adcd-147">**TestStructInStruct** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="8adcd-148">**TestStructInStruct3** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="8adcd-149">**TestArrayInStruct** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="8adcd-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) uygulamalar için daha önce listelenen işlevleri ve dört yapıları içeren özel bir yönetilmeyen kitaplığıdır: **MYPERSON**, **MYPERSON2**,  **MYPERSON3**, ve **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="8adcd-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="8adcd-151">Bu yapıları aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-151">These structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="8adcd-152">Yönetilen `MyPerson`, `MyPerson2`, `MyPerson3`, ve `MyArrayStruct` yapılarına aşağıdaki özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="8adcd-153">`MyPerson`yalnızca dize üyeler içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="8adcd-154">[CharSet](../../../docs/framework/interop/specifying-a-character-set.md) alan yönetilmeyen işleve geçirildiğinde ANSI biçimine dizeleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8adcd-154">The [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="8adcd-155">`MyPerson2`içeren bir **IntPtr** için `MyPerson` yapısı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="8adcd-156">**IntPtr** türü değiştirir özgün işaretçiyi yönetilmeyen yapısı için .NET Framework uygulamaları kodu işaretlenmemişse işaretçileri kullanmadığından **güvensiz**.</span><span class="sxs-lookup"><span data-stu-id="8adcd-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="8adcd-157">`MyPerson3`içeren `MyPerson` katıştırılmış yapısı olarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="8adcd-158">Başka bir yapı içinde katıştırılmış bir yapı doğrudan ana yapısına katıştırılmış yapısı öğelerini koyarak düzleştirilmiş veya katıştırılmış bir yapısı olarak, bu örnekte gibi bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="8adcd-159">`MyArrayStruct`dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="8adcd-160"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümelerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma değeri **ByValArray**, dizideki öğelerin sayısını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="8adcd-161">Bu örnekteki tüm yapıları için <xref:System.Runtime.InteropServices.StructLayoutAttribute> öznitelik üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="8adcd-162">`LibWrap` Sınıfı için yönetilen prototipleri içerir `TestStructInStruct`, `TestStructInStruct3`, ve `TestArrayInStruct` yöntemleri tarafından çağrılır `App` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="8adcd-163">Her prototip gibi tek bir parametre bildirir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="8adcd-164">`TestStructInStruct`türü için bir başvuru bildirir `MyPerson2` , parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="8adcd-165">`TestStructInStruct3`tür bildirir `MyPerson3` , parametre olarak ve parametre değerine göre geçirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="8adcd-166">`TestArrayInStruct`türü için bir başvuru bildirir `MyArrayStruct` , parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="8adcd-167">Yapıları parametresi içermedikçe yöntemleri bağımsız değişkenleri değere göre geçirilen **ref** (**ByRef** Visual Basic'te) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8adcd-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="8adcd-168">Örneğin, `TestStructInStruct` yöntemi geçirir türünde bir nesneye başvuru (bir adresi değeri) `MyPerson2` yönetilmeyen kod için.</span><span class="sxs-lookup"><span data-stu-id="8adcd-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="8adcd-169">Yapısını işlemek için `MyPerson2` noktaları için örnek belirtilen boyutta bir arabellek oluşturur ve birleştirerek adresini döndürür <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8adcd-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8adcd-170">Ardından, örnek yönetilmeyen arabellek yönetilen yapısı içeriği kopyalar.</span><span class="sxs-lookup"><span data-stu-id="8adcd-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="8adcd-171">Son olarak, örnek kullanır <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> yönetilen bir nesne için yönetilmeyen arabellek sıralama verilere yönteminden ve <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> yöntemi yönetilmeyen bellek bloğu boş.</span><span class="sxs-lookup"><span data-stu-id="8adcd-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="8adcd-172">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="8adcd-172">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a><span data-ttu-id="8adcd-173">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8adcd-173">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a><span data-ttu-id="8adcd-174">FindFile örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-174">FindFile sample</span></span>  
 <span data-ttu-id="8adcd-175">Bu örnek, yönetilmeyen bir işleve ikinci, katıştırılmış bir yapı içeren bir yapısı geçirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="8adcd-176">Ayrıca nasıl kullanılacağı ortaya <xref:System.Runtime.InteropServices.MarshalAsAttribute> yapısı içinde bir sabit uzunluk dizisi bildirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8adcd-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="8adcd-177">Bu örnekte, katıştırılmış yapı öğeleri üst yapısına eklenir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="8adcd-178">Katıştırılmış yapısının değil düzleştirilmiş bir örnek için bkz: [yapıları örnek](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span><span class="sxs-lookup"><span data-stu-id="8adcd-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span></span>  
  
 <span data-ttu-id="8adcd-179">FindFile örnek özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="8adcd-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="8adcd-180">**FindFirstFile** Kernel32.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-180">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="8adcd-181">İşleve özgün yapısı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-181">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="8adcd-182">Bu örnekte `FindData` sınıfı, karşılık gelen veri üyesi özgün yapısı ve katıştırılmış yapısı her öğe için içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="8adcd-183">İki özgün karakter arabellekleri yerine, sınıf dizelerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="8adcd-184">**MarshalAsAttribute** ayarlar <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunlukta karakter diziler yönetilmeyen yapılar içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="8adcd-185">`LibWrap` Sınıfı içeren yönetilen prototipi `FindFirstFile` geçirir yöntemi `FindData` bir parametre olarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-185">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="8adcd-186">Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreleri geçirildiğinden öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="8adcd-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="8adcd-187">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="8adcd-187">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a><span data-ttu-id="8adcd-188">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8adcd-188">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a><span data-ttu-id="8adcd-189">Birleşimler örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-189">Unions sample</span></span>  
 <span data-ttu-id="8adcd-190">Bu örnek yalnızca değer türleri içeren yapılar ve UNION bekleniyor bir yönetilmeyen işlevi için parametre olarak bir değer türü ve bir dize içeren yapıları geçirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="8adcd-191">UNION, iki veya daha fazla değişken tarafından paylaşılan bir bellek konumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8adcd-191">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="8adcd-192">Özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi, birleşimler örnek kullanır:</span><span class="sxs-lookup"><span data-stu-id="8adcd-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="8adcd-193">**TestUnion** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-193">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="8adcd-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) daha önce listelenen işlevi ve iki birleşimler için bir uygulama içeren özel bir yönetilmeyen kitaplık **MYUNION** ve **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="8adcd-194">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="8adcd-195">Birleşimler aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-195">The unions contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="8adcd-196">Yönetilen kodda birleşimler yapıları olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="8adcd-197">`MyUnion` Yapısı üye olarak iki değer türleri içerir: bir tamsayı ve bir double.</span><span class="sxs-lookup"><span data-stu-id="8adcd-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="8adcd-198"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, her veri üyesi kesin konumunu denetlemek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="8adcd-199"><xref:System.Runtime.InteropServices.FieldOffsetAttribute> Özniteliği, UNION yönetilmeyen gösterimini alanlarını fiziksel konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="8adcd-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="8adcd-200">Üyeleri aynı parça bellek tanımlayabilirsiniz böylece her iki üye aynı uzaklık değerleri sahip dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8adcd-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="8adcd-201">`MyUnion2_1`ve `MyUnion2_2` sırasıyla bir değer türü (tamsayı) ve bir dize içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="8adcd-202">Yönetilen kodda değer türleri ve başvuru türleri çakışmasına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8adcd-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="8adcd-203">Bu örnek aynı yönetilmeyen işlevi çağrılırken hem türlerini kullanmak arayan etkinleştirmek için aşırı yükleme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8adcd-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="8adcd-204">Düzenini `MyUnion2_1` açık olup kesin bir uzaklık değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="8adcd-205">Buna karşılık, `MyUnion2_2` bir ardışık düzen sahip olduğundan açık düzenleri başvuru türleriyle izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8adcd-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="8adcd-206"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Öznitelik kümelerini <xref:System.Runtime.InteropServices.UnmanagedType> numaralandırma **ByValTStr**, satır içi tanımlamak için kullanılan, sabit uzunlukta karakter diziler UNION yönetilmeyen gösterimini içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="8adcd-207">`LibWrap` Sınıfı için prototipleri içerir `TestUnion` ve `TestUnion2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8adcd-207">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="8adcd-208">`TestUnion2`bildirmek için aşırı `MyUnion2_1` veya `MyUnion2_2` parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="8adcd-209">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="8adcd-209">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a><span data-ttu-id="8adcd-210">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8adcd-210">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a><span data-ttu-id="8adcd-211">SysTime örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-211">SysTime sample</span></span>  
 <span data-ttu-id="8adcd-212">Bu örnek, bir işaretçi bir sınıf bir yapısına yönelik işaretçinin bekliyor yönetilmeyen bir işleve geçirilecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="8adcd-213">SysTime örnek özgün işlevi bildiriminden gösterilen aşağıdaki yönetilmeyen işlevi kullanır:</span><span class="sxs-lookup"><span data-stu-id="8adcd-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="8adcd-214">**GetSystemTime** Kernel32.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-214">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="8adcd-215">İşleve özgün yapısı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-215">The original structure passed to the function contains the following elements:</span></span>  
  
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
  
 <span data-ttu-id="8adcd-216">Bu örnekte `SystemTime` sınıfı sınıf üyeleri gösterilen özgün yapısı öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="8adcd-217"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği ayarlanmış üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olun.</span><span class="sxs-lookup"><span data-stu-id="8adcd-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="8adcd-218">`LibWrap` Sınıfı içeren yönetilen prototipi `GetSystemTime` geçirir yöntemi `SystemTime` sınıfı olarak bir giriş/çıkış parametresi varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-218">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="8adcd-219">Parametresi ile bildirilmelidir <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> başvuru türleri olan sınıfları, varsayılan olarak olduğu gibi parametreleri geçirildiğinden öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="8adcd-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="8adcd-220">Çağıran sonuçlarını almak için bu [yön öznitelikleri](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) açıkça uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-220">For the caller to receive the results, these [directional attributes](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) must be applied explicitly.</span></span> <span data-ttu-id="8adcd-221">`App` Sınıfının yeni bir örneğini oluşturur `SystemTime` sınıfı ve kendi veri alanları erişir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="8adcd-222">Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="8adcd-222">Code Samples</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="8adcd-223">OutArrayOfStructs örneği</span><span class="sxs-lookup"><span data-stu-id="8adcd-223">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="8adcd-224">Bu örnek nasıl tamsayılar ve Out parametreleri yönetilmeyen bir işleve dize olarak içeren bir dizi yapıların iletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="8adcd-225">Bu örnek kullanarak yerel bir işleve nasıl çağırılacağını <xref:System.Runtime.InteropServices.Marshal> sınıfı ve güvenli olmayan kod kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8adcd-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="8adcd-226">Bu örnek bir sarmalayıcı işlevleri kullanır ve platform çağırır tanımlanan [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), aynı zamanda sağlanan kaynak dosyalarında.</span><span class="sxs-lookup"><span data-stu-id="8adcd-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), also provided in the source files.</span></span> <span data-ttu-id="8adcd-227">Kullandığı `TestOutArrayOfStructs` işlevi ve `MYSTRSTRUCT2` yapısı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="8adcd-228">Yapısı aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8adcd-228">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="8adcd-229">`MyStruct` Sınıfı, bir dize nesnesi ANSI karakter içerir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="8adcd-230"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> Alan ANSI biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="8adcd-231">`MyUnsafeStruct`, bir yapı olduğundan içeren bir <xref:System.IntPtr> yerine bir dize türü.</span><span class="sxs-lookup"><span data-stu-id="8adcd-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="8adcd-232">`LibWrap` Sınıfı içeren aşırı yüklenmiş `TestOutArrayOfStructs` prototip yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adcd-232">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="8adcd-233">İle bir yöntem bir işaretçi bir parametre olarak bildirirse, sınıf işaretlenmelidir `unsafe` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8adcd-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="8adcd-234">Çünkü [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] güvenli olmayan kod, aşırı yüklenmiş yöntemin güvensiz değiştiricisi kullanamazsınız ve `MyUnsafeStruct` yapısı gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-234">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="8adcd-235">`App` Uygulayan sınıf `UsingMarshaling` dizi geçirmek için gerekli görevleri gerçekleştiren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adcd-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="8adcd-236">Dizi işaretlenmiş `out` (`ByRef` Visual Basic'te) verileri belirtmek için anahtar sözcüğü Aranan çağırana iletir.</span><span class="sxs-lookup"><span data-stu-id="8adcd-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="8adcd-237">Aşağıdaki uygulama kullanan <xref:System.Runtime.InteropServices.Marshal> sınıfı yöntemlerinin:</span><span class="sxs-lookup"><span data-stu-id="8adcd-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="8adcd-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A>yönetilen bir nesnenin yönetilmeyen arabellek verilerini sıralamakta.</span><span class="sxs-lookup"><span data-stu-id="8adcd-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="8adcd-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A>yapısında dizeler için ayrılan bellek serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="8adcd-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="8adcd-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>dizi için ayrılan bellek serbest bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="8adcd-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="8adcd-241">Daha önce belirtildiği gibi C# güvenli olmayan kod verir ve [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8adcd-241">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="8adcd-242">C# örneğinde, `UsingUnsafePointer` yerine işaretçileri kullanan alternatif bir yöntem uygulamasıdır <xref:System.Runtime.InteropServices.Marshal> geçirmek için sınıf geri dizi içeren `MyUnsafeStruct` yapısı.</span><span class="sxs-lookup"><span data-stu-id="8adcd-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="8adcd-243">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="8adcd-243">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a><span data-ttu-id="8adcd-244">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8adcd-244">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="8adcd-245">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8adcd-245">See Also</span></span>  
 [<span data-ttu-id="8adcd-246">Platform Çağırma ile veri hazırlama</span><span class="sxs-lookup"><span data-stu-id="8adcd-246">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="8adcd-247">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="8adcd-247">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="8adcd-248">Dizeleri hazırlama</span><span class="sxs-lookup"><span data-stu-id="8adcd-248">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="8adcd-249">Türlerin dizileri sıralama</span><span class="sxs-lookup"><span data-stu-id="8adcd-249">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)
