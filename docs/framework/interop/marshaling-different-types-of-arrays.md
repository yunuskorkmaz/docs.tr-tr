---
title: Farklı Dizi Türlerini Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: 1490171c4dd423baa3b6c5f5e00cf133c2584cae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124388"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="78259-102">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="78259-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="78259-103">Dizi, aynı türde bir veya daha fazla öğe içeren Yönetilen koddaki bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="78259-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="78259-104">Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="78259-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="78259-105">Bu davranış, yönetilen dizilerin ın/out parametreleri gibi yönetilen nesnelere geçirilme yöntemi ile tutarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="78259-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="78259-106">Daha fazla bilgi için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="78259-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="78259-107">Aşağıdaki tabloda diziler için sıralama seçenekleri listelenmekte ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78259-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="78259-108">dizide</span><span class="sxs-lookup"><span data-stu-id="78259-108">Array</span></span>|<span data-ttu-id="78259-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78259-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78259-110">Değere göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="78259-110">Of integers by value.</span></span>|<span data-ttu-id="78259-111">Bir tamsayılar dizisini ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="78259-112">Başvuruya göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="78259-112">Of integers by reference.</span></span>|<span data-ttu-id="78259-113">Bir tamsayı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="78259-114">Değere göre tamsayılar (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="78259-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="78259-115">Bir tamsayı matrisini bir ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="78259-116">Değere göre dizeler.</span><span class="sxs-lookup"><span data-stu-id="78259-116">Of strings by value.</span></span>|<span data-ttu-id="78259-117">Bir dize dizisini ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="78259-118">, Tamsayılar içeren yapılar.</span><span class="sxs-lookup"><span data-stu-id="78259-118">Of structures with integers.</span></span>|<span data-ttu-id="78259-119">As parametresi olarak tamsayılar içeren bir yapı dizisini geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="78259-120">Dizeleri olan yapılar.</span><span class="sxs-lookup"><span data-stu-id="78259-120">Of structures with strings.</span></span>|<span data-ttu-id="78259-121">Yalnızca dizeleri içeren bir yapı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="78259-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="78259-122">Dizi üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="78259-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78259-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="78259-123">Example</span></span>  
 <span data-ttu-id="78259-124">Bu örnek, aşağıdaki dizi türlerin nasıl geçirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="78259-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="78259-125">Değere göre tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="78259-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="78259-126">Başvuruya göre tamsayılar dizisi, yeniden boyutlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="78259-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="78259-127">Değere göre tamsayılar için çok boyutlu dizi (matris).</span><span class="sxs-lookup"><span data-stu-id="78259-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="78259-128">Değere göre dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="78259-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="78259-129">Tamsayılarla yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="78259-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="78259-130">Dizeler içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="78259-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="78259-131">Bir dizi başvuruya göre açıkça sıralanmamışsa, varsayılan davranış diziyi bir ın parametresi olarak sıraladığında.</span><span class="sxs-lookup"><span data-stu-id="78259-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="78259-132"><xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> özniteliklerini açıkça uygulayarak bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78259-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="78259-133">Diziler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="78259-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="78259-134">PInvokeLib. dll ' den alınan **Tebaşlangıçraylar** .</span><span class="sxs-lookup"><span data-stu-id="78259-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="78259-135">PInvokeLib. dll dosyasından **test edilmiş Testrefarray.**</span><span class="sxs-lookup"><span data-stu-id="78259-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="78259-136">PInvokeLib. dll dosyasından alınan **Testmatrixoflitre** .</span><span class="sxs-lookup"><span data-stu-id="78259-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="78259-137">**TestArrayOfStrings** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="78259-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="78259-138">PInvokeLib. dll dosyasından aktarılmış **Testarrayofyapılar** .</span><span class="sxs-lookup"><span data-stu-id="78259-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="78259-139">**TestArrayOfStructs2** , PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="78259-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="78259-140">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenen işlevler ve iki yapı değişkeni, **myPoint** ve **MyPerson**için uygulamalar içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="78259-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="78259-141">Yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="78259-141">The structures contain the following elements:</span></span>  
  
```cpp
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
  
 <span data-ttu-id="78259-142">Bu örnekte, `MyPoint` ve `MyPerson` yapıları gömülü türler içerir.</span><span class="sxs-lookup"><span data-stu-id="78259-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="78259-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="78259-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="78259-144">`NativeMethods` sınıfı, `App` sınıfı tarafından çağrılan bir yöntemler kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="78259-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="78259-145">Dizileri geçirme hakkında ayrıntılı bilgi için aşağıdaki örnekteki açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="78259-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="78259-146">Başvuru türü olan bir dizi, varsayılan olarak bir ın parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="78259-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="78259-147">Çağıranın sonuçları alması için, **InAttribute** ve **OutAttribute** 'un, diziyi içeren bağımsız değişkene açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78259-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="78259-148">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="78259-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="78259-149">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="78259-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="78259-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78259-150">See also</span></span>

- [<span data-ttu-id="78259-151">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="78259-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="78259-152">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="78259-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
