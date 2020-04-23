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
ms.openlocfilehash: c71c89e5797745144a2baed2d4846e3d9f9f26be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114014"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="8e5fa-102">Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama</span><span class="sxs-lookup"><span data-stu-id="8e5fa-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="8e5fa-103">Bu örnek, işlev işaretçileri bekleyen yönetilmeyen bir işleve temsilcilerin nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="8e5fa-104">Bir temsilci, bir yönteme başvuru tutan ve tür kullanımı uyumlu işlev işaretçisine veya geri çağırma işlevine eşdeğer olan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="8e5fa-105">Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı, bu çağrının süresi boyunca temsilciyi atık olarak toplanmaya karşı korur.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="8e5fa-106">Ancak, yönetilmeyen işlev çağrı tamamlandıktan sonra kullanmak üzere temsilciyi depoluyorsa, yönetilmeyen işlev temsilciyle bitene kadar çöp toplamayı el ile engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="8e5fa-107">Daha fazla bilgi için, bkz. [HandleRef örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) ve [GCHandle örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8e5fa-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="8e5fa-108">Geri çağırma örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="8e5fa-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="8e5fa-109">`TestCallBack`PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="8e5fa-110">`TestCallBack2`PInvokeLib. dll dosyasından verildi.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="8e5fa-111">[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , daha önce listelenen işlevler için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="8e5fa-112">Bu örnekte, `NativeMethods` sınıfı `TestCallBack` ve `TestCallBack2` yöntemleri için yönetilen prototürler içerir.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-112">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="8e5fa-113">Her iki yöntem de bir çağrı işlevine parametre olarak bir temsilci iletir.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="8e5fa-114">Temsilcinin imzası, başvurduğu yöntemin imzasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="8e5fa-115">Örneğin, `FPtr` ve `FPtr2` temsilcilerin `DoSomething` ve `DoSomething2` yöntemleriyle aynı olan imzaları vardır.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="8e5fa-116">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="8e5fa-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="8e5fa-117">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="8e5fa-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="8e5fa-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5fa-118">See also</span></span>

- <span data-ttu-id="8e5fa-119">[Çeşitli sıralama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e5fa-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="8e5fa-120">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="8e5fa-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="8e5fa-121">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8e5fa-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
