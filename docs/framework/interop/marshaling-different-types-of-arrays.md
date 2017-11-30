---
title: "Farklı Dizi Türlerini Sıralama"
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
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 157d157eceaa83893df3acf5efc9a8d4c1b27200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="ddbe2-102">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ddbe2-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="ddbe2-103">Bir dizi aynı türde bir veya daha fazla öğe içeriyor, yönetilen kodda bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="ddbe2-104">Diziler başvuru türleri olsa da, bunlar parametreler olduğu gibi yönetilmeyen işlevlerle iletilir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="ddbe2-105">Bu davranış, olan olarak In/Out parametreleri yönetilen diziler yönetilen nesnelere geçirilir şekilde tutmuyor.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="ddbe2-106">Daha fazla bilgi için bkz: [kopyalama ve sabitleme](../../../docs/framework/interop/copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="ddbe2-106">For additional details, see [Copying and Pinning](../../../docs/framework/interop/copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="ddbe2-107">Aşağıdaki tabloda dizileri sıralama seçeneklerini listeler ve bunların kullanım açıklar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="ddbe2-108">Dizi</span><span class="sxs-lookup"><span data-stu-id="ddbe2-108">Array</span></span>|<span data-ttu-id="ddbe2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddbe2-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ddbe2-110">Değere göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-110">Of integers by value.</span></span>|<span data-ttu-id="ddbe2-111">Dizisi bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ddbe2-112">Başvuruya göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-112">Of integers by reference.</span></span>|<span data-ttu-id="ddbe2-113">Dizisi bir giriş/çıkış parametre olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="ddbe2-114">Tamsayılar değerle (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="ddbe2-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="ddbe2-115">Tamsayıların bir matris bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ddbe2-116">Değere göre dizeleri.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-116">Of strings by value.</span></span>|<span data-ttu-id="ddbe2-117">Dize dizisi bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="ddbe2-118">Yapıları tamsayılı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-118">Of structures with integers.</span></span>|<span data-ttu-id="ddbe2-119">Bir dizi tamsayılar bir giriş parametresi olarak içeren yapılarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="ddbe2-120">Dizeler yapıları.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-120">Of structures with strings.</span></span>|<span data-ttu-id="ddbe2-121">Bir giriş/çıkış parametresi olarak yalnızca tamsayı içeren yapılarını dizisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="ddbe2-122">Dizi üyelerinin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ddbe2-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddbe2-123">Example</span></span>  
 <span data-ttu-id="ddbe2-124">Bu örnek, dizi aşağıdaki türlerini geçirmek gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ddbe2-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="ddbe2-125">Değere göre dizisi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="ddbe2-126">Yeniden boyutlandırılabilir başvuruya göre dizisi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="ddbe2-127">Çok boyutlu dizisi (Matris) değeri.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="ddbe2-128">Değere göre bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="ddbe2-129">Yapıları tamsayılı dizisi.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="ddbe2-130">Yapıları dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="ddbe2-131">Bir dizi açıkça başvuruya göre sıralanmış sürece, varsayılan davranışı dizi bir giriş parametresi olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="ddbe2-132">Uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> açıkça öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="ddbe2-133">Diziler örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="ddbe2-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="ddbe2-134">**TestArrayOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="ddbe2-135">**TestRefArrayOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="ddbe2-136">**TestMatrixOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="ddbe2-137">**TestArrayOfStrings** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="ddbe2-138">**TestArrayOfStructs** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="ddbe2-139">**TestArrayOfStructs2** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="ddbe2-140">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) daha önce listelenen işlevler ve iki yapı değişkenleri için uygulamaları içeren özel bir yönetilmeyen kitaplık **MYPOINT** ve **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-140">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="ddbe2-141">Yapıları aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ddbe2-141">The structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 <span data-ttu-id="ddbe2-142">Bu örnekte `MyPoint` ve `MyPerson` yapıları katıştırılmış türler içerir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="ddbe2-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği ayarlanmış üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olun.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="ddbe2-144">`LibWrap` Sınıfı içeren bir dizi yöntem tarafından çağrılır `App` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="ddbe2-145">Dizileri geçirme hakkında belirli Ayrıntılar için aşağıdaki örnek yer alan yorumlara bakın.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="ddbe2-146">Bir başvuru türü olan bir dizi varsayılan olarak bir giriş parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="ddbe2-147">Çağıran sonuçlarını almak için **InAttribute** ve **OutAttribute** dizi içeren bağımsız değişkeni açıkça uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ddbe2-148">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="ddbe2-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ddbe2-149">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="ddbe2-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="ddbe2-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ddbe2-150">See Also</span></span>  
 [<span data-ttu-id="ddbe2-151">Türlerin dizileri sıralama</span><span class="sxs-lookup"><span data-stu-id="ddbe2-151">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="ddbe2-152">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="ddbe2-152">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="ddbe2-153">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddbe2-153">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
