---
title: ICorDebugILFrame3::GetReturnValueForILOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="f452f-102">ICorDebugILFrame3::GetReturnValueForILOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="f452f-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="f452f-103">Bir işlevin dönüş değeri yalıtan bir "ICorDebugValue" nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="f452f-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f452f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f452f-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f452f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f452f-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="f452f-106">IL uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f452f-106">The IL offset.</span></span> <span data-ttu-id="f452f-107">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f452f-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="f452f-108">İşlev çağrısının dönüş değerini hakkında bilgi sağlayan bir "ICorDebugValue" arabirimi nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f452f-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f452f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f452f-109">Remarks</span></span>  
 <span data-ttu-id="f452f-110">Bu yöntem ile birlikte kullanılan [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir yönteminin dönüş değeri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f452f-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="f452f-111">Dönüş değerleri yoksayılır, aşağıdaki iki kod örneklerde olduğu gibi yöntemleri durumunda özellikle yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f452f-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="f452f-112">İlk örnek çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi, ancak yöntemin dönüş değeri yok sayıyor.</span><span class="sxs-lookup"><span data-stu-id="f452f-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="f452f-113">İkinci örnek hata ayıklama içinde daha yaygın bir sorun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f452f-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="f452f-114">Yöntem çağrısı bir bağımsız değişken olarak kullanılan bir yöntem için dönüş değerini yalnızca hata ayıklayıcı çağrılan yöntemin adımları zaman erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f452f-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="f452f-115">Özellikle çağrılan yöntemi bir harici kitaplık tanımlandığında çoğu durumda, mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="f452f-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="f452f-116">Geçirirseniz [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir işlev çağrısı siteye uzaklığı IL bir yöntemi, bir veya daha fazla yerel uzaklıklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f452f-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="f452f-117">Hata ayıklayıcı kesme noktaları bu yerel uzaklıkları işlevinde sonra ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f452f-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="f452f-118">Hata ayıklayıcı kesme noktaları geldiğinde dönüş değeri almak için bu yönteme geçirilen aynı IL uzaklığı sonra geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f452f-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="f452f-119">Hata ayıklayıcı sonra ayarlayın kesme noktaları temizlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f452f-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f452f-120">[Icordebugcode3::getreturnvalueliveoffset yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri dönüş değeri bilgilerini edinin izin verir.</span><span class="sxs-lookup"><span data-stu-id="f452f-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="f452f-121">Değer türlerinden dönüş değeri bilgileri alınıyor (diğer bir deyişle, türetilen tüm türleri <xref:System.ValueType>) desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="f452f-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="f452f-122">Tarafından belirtilen IL uzaklığı `ILOffset` parametresi bir işlev çağrısı sitede olmalıdır ve ayıklayıcı tarafından döndürülen yerel uzaklığında bir kesme adresindeki durdurulmalıdır [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f452f-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="f452f-123">Belirtilen IL uzaklığı için doğru konumda ayıklayıcı durdurulmaz API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f452f-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="f452f-124">İşlev çağrısı bir değer döndürmüyor API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f452f-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="f452f-125">`ICorDebugILFrame3::GetReturnValueForILOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemleri.</span><span class="sxs-lookup"><span data-stu-id="f452f-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f452f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f452f-126">Requirements</span></span>  
 <span data-ttu-id="f452f-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f452f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f452f-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f452f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f452f-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f452f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f452f-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f452f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f452f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f452f-131">See Also</span></span>  
 [<span data-ttu-id="f452f-132">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f452f-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [<span data-ttu-id="f452f-133">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f452f-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
