---
title: Farklı Dizi Türlerini Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2a4b91608306021ce510098eaf044520cbb089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391462"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="9656d-102">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="9656d-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="9656d-103">Bir dizi aynı türde bir veya daha fazla öğe içeriyor, yönetilen kodda bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="9656d-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="9656d-104">Diziler başvuru türleri olsa da, bunlar parametreler olduğu gibi yönetilmeyen işlevlerle iletilir.</span><span class="sxs-lookup"><span data-stu-id="9656d-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="9656d-105">Bu davranış, olan olarak In/Out parametreleri yönetilen diziler yönetilen nesnelere geçirilir şekilde tutmuyor.</span><span class="sxs-lookup"><span data-stu-id="9656d-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="9656d-106">Daha fazla bilgi için bkz: [kopyalama ve sabitleme](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="9656d-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="9656d-107">Aşağıdaki tabloda dizileri sıralama seçeneklerini listeler ve bunların kullanım açıklar.</span><span class="sxs-lookup"><span data-stu-id="9656d-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="9656d-108">Dizi</span><span class="sxs-lookup"><span data-stu-id="9656d-108">Array</span></span>|<span data-ttu-id="9656d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9656d-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9656d-110">Değere göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="9656d-110">Of integers by value.</span></span>|<span data-ttu-id="9656d-111">Dizisi bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="9656d-112">Başvuruya göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="9656d-112">Of integers by reference.</span></span>|<span data-ttu-id="9656d-113">Dizisi bir giriş/çıkış parametre olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="9656d-114">Tamsayılar değerle (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="9656d-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="9656d-115">Tamsayıların bir matris bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="9656d-116">Değere göre dizeleri.</span><span class="sxs-lookup"><span data-stu-id="9656d-116">Of strings by value.</span></span>|<span data-ttu-id="9656d-117">Dize dizisi bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="9656d-118">Yapıları tamsayılı.</span><span class="sxs-lookup"><span data-stu-id="9656d-118">Of structures with integers.</span></span>|<span data-ttu-id="9656d-119">Bir dizi tamsayılar bir giriş parametresi olarak içeren yapılarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="9656d-120">Dizeler yapıları.</span><span class="sxs-lookup"><span data-stu-id="9656d-120">Of structures with strings.</span></span>|<span data-ttu-id="9656d-121">Bir giriş/çıkış parametresi olarak yalnızca tamsayı içeren yapılarını dizisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="9656d-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="9656d-122">Dizi üyelerinin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9656d-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9656d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9656d-123">Example</span></span>  
 <span data-ttu-id="9656d-124">Bu örnek, dizi aşağıdaki türlerini geçirmek gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9656d-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="9656d-125">Değere göre dizisi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="9656d-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="9656d-126">Yeniden boyutlandırılabilir başvuruya göre dizisi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="9656d-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="9656d-127">Çok boyutlu dizisi (Matris) değeri.</span><span class="sxs-lookup"><span data-stu-id="9656d-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="9656d-128">Değere göre bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9656d-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="9656d-129">Yapıları tamsayılı dizisi.</span><span class="sxs-lookup"><span data-stu-id="9656d-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="9656d-130">Yapıları dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9656d-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="9656d-131">Bir dizi açıkça başvuruya göre sıralanmış sürece, varsayılan davranışı dizi bir giriş parametresi olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="9656d-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="9656d-132">Uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> açıkça öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="9656d-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="9656d-133">Diziler örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="9656d-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="9656d-134">**TestArrayOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="9656d-135">**TestRefArrayOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="9656d-136">**TestMatrixOfInts** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="9656d-137">**TestArrayOfStrings** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="9656d-138">**TestArrayOfStructs** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="9656d-139">**TestArrayOfStructs2** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="9656d-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="9656d-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) daha önce listelenen işlevler ve iki yapı değişkenleri için uygulamaları içeren özel bir yönetilmeyen kitaplık **MYPOINT** ve **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="9656d-140">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="9656d-141">Yapıları aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="9656d-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="9656d-142">Bu örnekte `MyPoint` ve `MyPerson` yapıları katıştırılmış türler içerir.</span><span class="sxs-lookup"><span data-stu-id="9656d-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="9656d-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği ayarlanmış üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olun.</span><span class="sxs-lookup"><span data-stu-id="9656d-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="9656d-144">`LibWrap` Sınıfı içeren bir dizi yöntem tarafından çağrılır `App` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9656d-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="9656d-145">Dizileri geçirme hakkında belirli Ayrıntılar için aşağıdaki örnek yer alan yorumlara bakın.</span><span class="sxs-lookup"><span data-stu-id="9656d-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="9656d-146">Bir başvuru türü olan bir dizi varsayılan olarak bir giriş parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9656d-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="9656d-147">Çağıran sonuçlarını almak için **InAttribute** ve **OutAttribute** dizi içeren bağımsız değişkeni açıkça uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9656d-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="9656d-148">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="9656d-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="9656d-149">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="9656d-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="9656d-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9656d-150">See Also</span></span>  
 <span data-ttu-id="9656d-151">[Türlerin dizileri sıralama](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9656d-151">[Marshaling Arrays of Types](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))</span></span>  
 <span data-ttu-id="9656d-152">[Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9656d-152">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="9656d-153">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9656d-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
