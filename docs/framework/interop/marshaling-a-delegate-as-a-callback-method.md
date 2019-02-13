---
title: Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23079343244c8471f9ae5ff0a7613d0d8a84242b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219743"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="afc53-102">Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama</span><span class="sxs-lookup"><span data-stu-id="afc53-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="afc53-103">Bu örnek, temsilciler işlev işaretçileri bekleniyor yönetilmeyen bir işleve geçirilecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="afc53-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="afc53-104">Bir temsilci, bir yönteme başvuru içerebilir ve bir tür açısından güvenli bir işlev işaretçisine veya geri çağırma işlevi için eşdeğer bir gruba bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="afc53-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afc53-105">Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı bu çağrı süresi boyunca toplanan atık olarak temsilci korur.</span><span class="sxs-lookup"><span data-stu-id="afc53-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="afc53-106">Yönetilmeyen işlev çağrısı tamamlandıktan sonra kullanmak için temsilci depoluyorsa, temsilci ile yönetilmeyen işlev tamamlanana kadar ancak el ile çöp toplama önlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="afc53-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="afc53-107">Daha fazla bilgi için [HandleRef örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) ve [GCHandle örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="afc53-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>  
  
 <span data-ttu-id="afc53-108">Geri çağırma örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="afc53-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="afc53-109">**TestCallBack** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="afc53-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="afc53-110">**TestCallBack2** Pinvokelib.DLL'den dışarı.</span><span class="sxs-lookup"><span data-stu-id="afc53-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="afc53-111">[PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) daha önce listelenen işlevlerin için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="afc53-111">[PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="afc53-112">Bu örnekte `LibWrap` sınıfı için yönetilen prototipleri içeren `TestCallBack` ve `TestCallBack2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="afc53-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="afc53-113">Her iki yöntem de bir temsilci, bir parametre olarak bir geri çağırma işlevine geçirin.</span><span class="sxs-lookup"><span data-stu-id="afc53-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="afc53-114">Metot temsilcisinin imzası başvurduğu metodun imzası eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="afc53-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="afc53-115">Örneğin, `FPtr` ve `FPtr2` temsilciler sahip aynı imza `DoSomething` ve `DoSomething2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="afc53-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="afc53-116">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="afc53-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="afc53-117">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="afc53-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="afc53-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afc53-118">See also</span></span>
- <span data-ttu-id="afc53-119">[Çeşitli sıralama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="afc53-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- <span data-ttu-id="afc53-120">[Platform çağırma veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ac7ay120(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="afc53-120">[Platform Invoke Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ac7ay120(v=vs.100))</span></span>
- [<span data-ttu-id="afc53-121">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="afc53-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
