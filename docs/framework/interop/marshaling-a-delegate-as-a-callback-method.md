---
title: Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama
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
ms.openlocfilehash: ff875f2807a14493ab81a9e354b5c4dcdf3d5feb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389390"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="0cedf-102">Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama</span><span class="sxs-lookup"><span data-stu-id="0cedf-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="0cedf-103">Bu örnek nasıl temsilciler işlev işaretçileri bekleniyor yönetilmeyen bir işleve nasıl iletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cedf-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="0cedf-104">Temsilci bir yöntem başvuru içerebilir ve bir tür kullanımı uyumlu işlev işaretçisi ya da bir geri çağırma işlevini eşdeğer olan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0cedf-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cedf-105">Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı bu çağrı boyunca toplanan çöp olmaktan temsilci korur.</span><span class="sxs-lookup"><span data-stu-id="0cedf-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="0cedf-106">Yönetilmeyen işlev çağrısı tamamlandıktan sonra kullanmak için temsilci depoluyorsa, temsilci ile yönetilmeyen işlev tamamlanana kadar ancak, el ile çöp toplama engellemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cedf-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="0cedf-107">Daha fazla bilgi için bkz: [HandleRef örnek](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) ve [GCHandle örnek](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0cedf-107">For more information, see the [HandleRef Sample](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) and [GCHandle Sample](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span></span>  
  
 <span data-ttu-id="0cedf-108">Geri arama örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="0cedf-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="0cedf-109">**TestCallBack** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="0cedf-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="0cedf-110">**TestCallBack2** PinvokeLib.dll dışarı.</span><span class="sxs-lookup"><span data-stu-id="0cedf-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="0cedf-111">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) daha önce listelenen işlevleri için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="0cedf-111">[PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="0cedf-112">Bu örnekte `LibWrap` sınıfı için yönetilen prototipleri içerir `TestCallBack` ve `TestCallBack2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0cedf-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="0cedf-113">Her iki yöntem de bir temsilci için bir geri çağırma işlevi parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="0cedf-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="0cedf-114">Temsilci imza başvurduğu yöntemi imzası eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0cedf-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="0cedf-115">Örneğin, `FPtr` ve `FPtr2` temsilciler sahip aynı imza `DoSomething` ve `DoSomething2` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0cedf-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="0cedf-116">Prototipleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="0cedf-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="0cedf-117">İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="0cedf-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="0cedf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0cedf-118">See Also</span></span>  
 <span data-ttu-id="0cedf-119">[Çeşitli hazırlama örnekleri](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0cedf-119">[Miscellaneous Marshaling Samples](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span></span>  
 <span data-ttu-id="0cedf-120">[Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0cedf-120">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="0cedf-121">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cedf-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
