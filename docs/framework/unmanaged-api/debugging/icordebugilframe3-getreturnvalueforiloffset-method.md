---
title: ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178811"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="9552b-102">ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9552b-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="9552b-103">Bir işlevin geri dönüş değerini kapsülleyen bir "ICorDebugValue" nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="9552b-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9552b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9552b-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9552b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9552b-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="9552b-106">IL ofset.</span><span class="sxs-lookup"><span data-stu-id="9552b-106">The IL offset.</span></span> <span data-ttu-id="9552b-107">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9552b-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="9552b-108">İşlev çağrısının geri dönüş değeri hakkında bilgi sağlayan "ICorDebugValue" arabirimi nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9552b-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9552b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9552b-109">Remarks</span></span>  
 <span data-ttu-id="9552b-110">Bu yöntem, bir yöntemin geri dönüş değerini almak için [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9552b-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="9552b-111">Özellikle, aşağıdaki iki kod örneğinde olduğu gibi, iade değerleri göz ardı edilen yöntemler de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9552b-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="9552b-112">İlk örnek <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi çağırır, ancak yöntemin geri dönüş değerini yoksa.</span><span class="sxs-lookup"><span data-stu-id="9552b-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="9552b-113">İkinci örnek, hata ayıklamada çok daha yaygın bir sorunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9552b-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="9552b-114">Yöntem çağrısında bağımsız değişken olarak kullanıldığından, geri dönüş değerine yalnızca çağrıyı çağıran yöntem üzerinden hata ayıklama adımı attığında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9552b-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="9552b-115">Birçok durumda, özellikle çağrılan yöntem dış kitaplıkta tanımlandığında, bu mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="9552b-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="9552b-116">[ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemini bir işlev arama sitesine IL ofset'i geçerseniz, bir veya daha fazla yerel uzaklık döndürür.</span><span class="sxs-lookup"><span data-stu-id="9552b-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="9552b-117">Hata ayıklama, işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9552b-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="9552b-118">Hata ayıklama kesme noktalarından birine çarptığında, iade değerini almak için bu yönteme geçtiğiniz IL ofsetini geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9552b-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="9552b-119">Hata ayıklama daha sonra ayarladığının tüm kesme noktalarını temizlemelidir.</span><span class="sxs-lookup"><span data-stu-id="9552b-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9552b-120">[ICorDebugCode3::GetReturnValueLiveOffset Yöntemi](icordebugcode3-getreturnvalueliveoffset-method.md) `ICorDebugILFrame3::GetReturnValueForILOffset` ve yöntemleri yalnızca başvuru türleri için iade değeri bilgileri almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9552b-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="9552b-121">İade değeri bilgilerinin değer türlerinden (diğer bir şekilde) <xref:System.ValueType>alınması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9552b-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="9552b-122">`ILOffset` Parametre tarafından belirtilen IL ofset bir işlev arama sitesinde olmalıdır ve hata ayıklama iCorDebugCode3 tarafından döndürülen yerli ofset bir kesme noktasında [ayarlanmalıdır::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL ofset için.</span><span class="sxs-lookup"><span data-stu-id="9552b-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="9552b-123">Hata ayıklama belirtilen IL ofset için doğru konumda durdurulmazsa, API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9552b-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="9552b-124">İşlev çağrısı bir değer döndürmezse, API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9552b-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="9552b-125">Bu `ICorDebugILFrame3::GetReturnValueForILOffset` yöntem yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9552b-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9552b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9552b-126">Requirements</span></span>  
 <span data-ttu-id="9552b-127">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9552b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9552b-128">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9552b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9552b-129">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9552b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9552b-130">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9552b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9552b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9552b-131">See also</span></span>

- [<span data-ttu-id="9552b-132">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9552b-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="9552b-133">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9552b-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
