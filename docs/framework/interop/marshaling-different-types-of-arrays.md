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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cafb15f691daa8d0d0e6c1ebab3cb89f7c811612
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642858"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="39110-102">Farklı Dizi Türlerini Hazırlama</span><span class="sxs-lookup"><span data-stu-id="39110-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="39110-103">Bir dizi aynı türden bir veya daha fazla öğe içeriyor, yönetilen kodda bir başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="39110-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="39110-104">Diziler başvuru türleri olsa da, olduğu gibi parametreleri yönetilmeyen bir işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39110-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="39110-105">Bu davranış, In/Out parametreleri olan yönetilen nesnelere, yönetilen diziler geçirilen yolu ile tutarsız.</span><span class="sxs-lookup"><span data-stu-id="39110-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="39110-106">Ek ayrıntılar için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="39110-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="39110-107">Aşağıdaki tabloda, dizileri sıralama seçeneklerini listeler ve bunların kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="39110-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="39110-108">Dizi</span><span class="sxs-lookup"><span data-stu-id="39110-108">Array</span></span>|<span data-ttu-id="39110-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39110-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39110-110">Değere göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="39110-110">Of integers by value.</span></span>|<span data-ttu-id="39110-111">Tamsayı dizisi, bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="39110-112">Başvuruya göre tamsayılar.</span><span class="sxs-lookup"><span data-stu-id="39110-112">Of integers by reference.</span></span>|<span data-ttu-id="39110-113">Tamsayı dizisi bir ın/Out parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="39110-114">Tamsayılar değeriyle (iki boyutlu).</span><span class="sxs-lookup"><span data-stu-id="39110-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="39110-115">Matris tamsayı bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="39110-116">Değere göre dizeleri.</span><span class="sxs-lookup"><span data-stu-id="39110-116">Of strings by value.</span></span>|<span data-ttu-id="39110-117">Dizelerden oluşan bir dizi bir giriş parametresi olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="39110-118">Yapıları ile tamsayı.</span><span class="sxs-lookup"><span data-stu-id="39110-118">Of structures with integers.</span></span>|<span data-ttu-id="39110-119">Bir dizi bir giriş parametresi olarak tamsayılar içeren yapılarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="39110-120">Yapıları dizeler.</span><span class="sxs-lookup"><span data-stu-id="39110-120">Of structures with strings.</span></span>|<span data-ttu-id="39110-121">Yalnızca dizelere bir ın/Out parametresi olarak içeren yapılarını dizisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="39110-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="39110-122">Dizi üyelerinin değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="39110-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39110-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="39110-123">Example</span></span>  
 <span data-ttu-id="39110-124">Bu örnek, dizileri aşağıdaki türleri nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="39110-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="39110-125">Değer tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="39110-125">Array of integers by value.</span></span>  
  
- <span data-ttu-id="39110-126">Yeniden boyutlandırılabilir başvuruya göre tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="39110-126">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="39110-127">Tamsayı değerine göre çok boyutlu dizisi (matrix).</span><span class="sxs-lookup"><span data-stu-id="39110-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="39110-128">Değer bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="39110-128">Array of strings by value.</span></span>  
  
- <span data-ttu-id="39110-129">Yapıları ile tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="39110-129">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="39110-130">Yapıları dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="39110-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="39110-131">Bir dizi başvuruya göre açıkça sıralanır sürece, varsayılan davranışı dizi bir giriş parametresi olarak sürekliliğe devreder.</span><span class="sxs-lookup"><span data-stu-id="39110-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="39110-132">Uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> açıkça öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="39110-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="39110-133">Diziler örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="39110-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="39110-134">**TestArrayOfInts** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="39110-135">**TestRefArrayOfInts** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="39110-136">**TestMatrixOfInts** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="39110-137">**TestArrayOfStrings** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="39110-138">**TestArrayOfStructs** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="39110-139">**TestArrayOfStructs2** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="39110-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="39110-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) daha önce listelenen işlevlerin ve iki yapı değişkenleri için uygulamaları içeren özel bir yönetilmeyen kitaplıktır **MYPOINT** ve **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="39110-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="39110-141">Yapılar aşağıdaki öğeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="39110-141">The structures contain the following elements:</span></span>  
  
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
  
 <span data-ttu-id="39110-142">Bu örnekte `MyPoint` ve `MyPerson` yapıları katıştırılmış türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="39110-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="39110-143"><xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="39110-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="39110-144">`LibWrap` Sınıfı içeren bir dizi çağıran yöntem `App` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39110-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="39110-145">Dizileri geçirme hakkında belirli bilgiler için aşağıdaki örnekte yer alan yorumlara bakın.</span><span class="sxs-lookup"><span data-stu-id="39110-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="39110-146">Bir başvuru türü bir dizi varsayılan olarak bir giriş parametresi olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="39110-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="39110-147">Sonuçları almak çağırıcı için **InAttribute** ve **OutAttribute** diziyi içeren bir bağımsız değişken için açıkça uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39110-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="39110-148">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="39110-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="39110-149">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="39110-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="39110-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39110-150">See also</span></span>

- [<span data-ttu-id="39110-151">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="39110-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="39110-152">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39110-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
