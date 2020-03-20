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
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181361"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="b6315-102">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="b6315-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="b6315-103">Dizi, yönetilen kodda aynı türden bir veya daha fazla öğe içeren bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="b6315-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="b6315-104">Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametreler olarak geçirilirler.</span><span class="sxs-lookup"><span data-stu-id="b6315-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="b6315-105">Bu davranış, yönetilen dizilerin yönetilen nesnelere geçirildiği ve In/Out parametreleri olarak geçirildiğiyle tutarsızdır.</span><span class="sxs-lookup"><span data-stu-id="b6315-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="b6315-106">Ek ayrıntılar için [bkz.](copying-and-pinning.md)</span><span class="sxs-lookup"><span data-stu-id="b6315-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="b6315-107">Aşağıdaki tabloda diziler için mareşal seçenekleri listelanır ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b6315-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="b6315-108">Dizi</span><span class="sxs-lookup"><span data-stu-id="b6315-108">Array</span></span>|<span data-ttu-id="b6315-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6315-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6315-110">Değere göre tümsadanların.</span><span class="sxs-lookup"><span data-stu-id="b6315-110">Of integers by value.</span></span>|<span data-ttu-id="b6315-111">Bir in parametresi olarak bir dizi tümseci geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="b6315-112">Referans olarak tümsadanların.</span><span class="sxs-lookup"><span data-stu-id="b6315-112">Of integers by reference.</span></span>|<span data-ttu-id="b6315-113">Bir dizi integer'ı Giriş/Çıkış parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="b6315-114">Değere göre tümsaderlerin (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="b6315-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="b6315-115">Tamsayılar matrisini In parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="b6315-116">Dizilerin değerine göre.</span><span class="sxs-lookup"><span data-stu-id="b6315-116">Of strings by value.</span></span>|<span data-ttu-id="b6315-117">Bir dizi dizeyi In parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="b6315-118">İntegerli yapıların.</span><span class="sxs-lookup"><span data-stu-id="b6315-118">Of structures with integers.</span></span>|<span data-ttu-id="b6315-119">In parametresi olarak, içinde hiçsesayı içeren bir dizi yapıyı geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="b6315-120">Dizeleri olan yapıların.</span><span class="sxs-lookup"><span data-stu-id="b6315-120">Of structures with strings.</span></span>|<span data-ttu-id="b6315-121">Yalnızca Giriş/Çıkış parametresi olarak dizeleri içeren bir dizi yapıyı geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6315-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="b6315-122">Dizinin üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6315-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6315-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6315-123">Example</span></span>  
 <span data-ttu-id="b6315-124">Bu örnek, aşağıdaki dizi türlerinin nasıl geçirilen gösteriş gösterir:</span><span class="sxs-lookup"><span data-stu-id="b6315-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="b6315-125">Değere göre tümerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6315-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="b6315-126">Yeniden boyutlandırılabilen başvuru yaylaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6315-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="b6315-127">Değere göre çok boyutlu dizi (matris).</span><span class="sxs-lookup"><span data-stu-id="b6315-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="b6315-128">Değere göre dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6315-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="b6315-129">Tümsegeriçeren yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6315-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="b6315-130">Dizeleri ile yapıların dizi.</span><span class="sxs-lookup"><span data-stu-id="b6315-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="b6315-131">Bir dizi açıkça başvuru tarafından marshaled sürece, varsayılan davranış bir In parametresi olarak dizi marshals.</span><span class="sxs-lookup"><span data-stu-id="b6315-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="b6315-132">Bu davranışı <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleri açıkça uygulayarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6315-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="b6315-133">Diziler örneği, özgün işlev bildirimiile gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="b6315-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="b6315-134">PinvokeLib.dll'den ihraç edilen **TestArrayOfInts.**</span><span class="sxs-lookup"><span data-stu-id="b6315-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="b6315-135">**TestRefArrayOfInts** PinvokeLib.dll ihraç.</span><span class="sxs-lookup"><span data-stu-id="b6315-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="b6315-136">PinvokeLib.dll'den ihraç edilen **TestMatrixOfInts.**</span><span class="sxs-lookup"><span data-stu-id="b6315-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="b6315-137">PinvokeLib.dll'den dışa aktarılan **TestArrayOfStrings.**</span><span class="sxs-lookup"><span data-stu-id="b6315-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="b6315-138">PinvokeLib.dll'den ihraç edilen **TestArrayOfStructs.**</span><span class="sxs-lookup"><span data-stu-id="b6315-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="b6315-139">**TestArrayOfStructs2** PinvokeLib.dll'den ihraç edildi.</span><span class="sxs-lookup"><span data-stu-id="b6315-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="b6315-140">[PinvokeLib.dll,](marshaling-data-with-platform-invoke.md#pinvokelibdll) daha önce listelenen işlevler ve **MYPOINT** ve **MYPERSON**olmak üzere iki yapı değişkeni için uygulamalar içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="b6315-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="b6315-141">Yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b6315-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="b6315-142">Bu örnekte, `MyPoint` `MyPerson` ve yapılar gömülü türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b6315-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="b6315-143">Öznitelik, <xref:System.Runtime.InteropServices.StructLayoutAttribute> üyelerin göründükleri sırada, sırayla bellekte düzenlendiğinden emin olmak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b6315-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="b6315-144">Sınıf, `NativeMethods` `App` sınıf tarafından çağrılan bir dizi yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="b6315-144">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="b6315-145">Geçen diziler hakkında özel ayrıntılar için aşağıdaki örnekteki yorumlara bakın.</span><span class="sxs-lookup"><span data-stu-id="b6315-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="b6315-146">Başvuru türü olan bir dizi varsayılan olarak In parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b6315-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="b6315-147">Arayanın sonuçları alabilmesi için, diziyi içeren bağımsız değişkene açık olarak **InAttribute** ve **OutAttribute** uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6315-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="b6315-148">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="b6315-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="b6315-149">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="b6315-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="b6315-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6315-150">See also</span></span>

- [<span data-ttu-id="b6315-151">Platform çağrıcı veri türleri</span><span class="sxs-lookup"><span data-stu-id="b6315-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="b6315-152">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6315-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
