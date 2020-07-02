---
title: Farklı Dizi Türlerini Hazırlama
description: Değer veya başvuruya göre tamsayılar, değere göre 2 boyutlu tamsayılar, değere göre dizeler ve tamsayı veya dizeler içeren yapılar gibi farklı dizi türlerini sıralama.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621502"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="c12e4-103">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c12e4-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="c12e4-104">Dizi, aynı türde bir veya daha fazla öğe içeren Yönetilen koddaki bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="c12e4-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="c12e4-105">Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="c12e4-106">Bu davranış, yönetilen dizilerin ın/out parametreleri gibi yönetilen nesnelere geçirilme yöntemi ile tutarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="c12e4-107">Daha fazla bilgi için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="c12e4-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="c12e4-108">Aşağıdaki tabloda diziler için sıralama seçenekleri listelenmekte ve kullanımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c12e4-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="c12e4-109">Dizi</span><span class="sxs-lookup"><span data-stu-id="c12e4-109">Array</span></span>|<span data-ttu-id="c12e4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c12e4-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c12e4-111">Değere göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="c12e4-111">Of integers by value.</span></span>|<span data-ttu-id="c12e4-112">Bir tamsayılar dizisini ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="c12e4-113">Başvuruya göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="c12e4-113">Of integers by reference.</span></span>|<span data-ttu-id="c12e4-114">Bir tamsayı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="c12e4-115">Değere göre tamsayılar (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="c12e4-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="c12e4-116">Bir tamsayı matrisini bir ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="c12e4-117">Değere göre dizeler.</span><span class="sxs-lookup"><span data-stu-id="c12e4-117">Of strings by value.</span></span>|<span data-ttu-id="c12e4-118">Bir dize dizisini ın parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="c12e4-119">, Tamsayılar içeren yapılar.</span><span class="sxs-lookup"><span data-stu-id="c12e4-119">Of structures with integers.</span></span>|<span data-ttu-id="c12e4-120">As parametresi olarak tamsayılar içeren bir yapı dizisini geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="c12e4-121">Dizeleri olan yapılar.</span><span class="sxs-lookup"><span data-stu-id="c12e4-121">Of structures with strings.</span></span>|<span data-ttu-id="c12e4-122">Yalnızca dizeleri içeren bir yapı dizisini bir ın/out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="c12e4-123">Dizi üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c12e4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="c12e4-124">Example</span></span>  
 <span data-ttu-id="c12e4-125">Bu örnek, aşağıdaki dizi türlerin nasıl geçirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c12e4-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="c12e4-126">Değere göre tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="c12e4-127">Başvuruya göre tamsayılar dizisi, yeniden boyutlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="c12e4-128">Değere göre tamsayılar için çok boyutlu dizi (matris).</span><span class="sxs-lookup"><span data-stu-id="c12e4-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="c12e4-129">Değere göre dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="c12e4-130">Tamsayılarla yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="c12e4-131">Dizeler içeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="c12e4-132">Bir dizi başvuruya göre açıkça sıralanmamışsa, varsayılan davranış diziyi bir ın parametresi olarak sıraladığında.</span><span class="sxs-lookup"><span data-stu-id="c12e4-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="c12e4-133"><xref:System.Runtime.InteropServices.InAttribute>Ve özniteliklerini açıkça uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c12e4-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="c12e4-134">Diziler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="c12e4-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="c12e4-135">PinvokeLib.dll 'den alınan **Testarrayofi** .</span><span class="sxs-lookup"><span data-stu-id="c12e4-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="c12e4-136">PinvokeLib.dll 'den dışarıya gelen **Testrefarrayoftri** .</span><span class="sxs-lookup"><span data-stu-id="c12e4-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="c12e4-137">PinvokeLib.dll 'den dışarıya gelen **Testmatrixoflitre** .</span><span class="sxs-lookup"><span data-stu-id="c12e4-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="c12e4-138">**TestArrayOfStrings** PinvokeLib.dll 'dan verildi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="c12e4-139">PinvokeLib.dll 'den dışarıya gelen **Testarrayofyapılar** .</span><span class="sxs-lookup"><span data-stu-id="c12e4-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="c12e4-140">**TestArrayOfStructs2** PinvokeLib.dll dışarıya verildi.</span><span class="sxs-lookup"><span data-stu-id="c12e4-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="c12e4-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenen işlevler ve iki yapı değişkeni, **myPoint** ve **MyPerson**için uygulamalar içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="c12e4-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="c12e4-142">Yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="c12e4-142">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="c12e4-143">Bu örnekte, `MyPoint` ve `MyPerson` yapıları gömülü türler içerir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="c12e4-144"><xref:System.Runtime.InteropServices.StructLayoutAttribute>Özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c12e4-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="c12e4-145">`NativeMethods`Sınıfı, sınıfı tarafından çağrılan bir yöntemler kümesi içerir `App` .</span><span class="sxs-lookup"><span data-stu-id="c12e4-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="c12e4-146">Dizileri geçirme hakkında ayrıntılı bilgi için aşağıdaki örnekteki açıklamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="c12e4-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="c12e4-147">Başvuru türü olan bir dizi, varsayılan olarak bir ın parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="c12e4-148">Çağıranın sonuçları alması için, **InAttribute** ve **OutAttribute** 'un, diziyi içeren bağımsız değişkene açıkça uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c12e4-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="c12e4-149">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="c12e4-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="c12e4-150">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="c12e4-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="c12e4-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c12e4-151">See also</span></span>

- [<span data-ttu-id="c12e4-152">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="c12e4-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="c12e4-153">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c12e4-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
