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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ac90473a0bf15173683c45abc8e4a840ea7e733
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088307"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="3126b-102">ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3126b-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>
<span data-ttu-id="3126b-103">Bir işlevin dönüş değeri bir "ICorDebugValue" nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="3126b-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3126b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3126b-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3126b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3126b-105">Parameters</span></span>  
 `ILOffset`  
 <span data-ttu-id="3126b-106">IL uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="3126b-106">The IL offset.</span></span> <span data-ttu-id="3126b-107">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3126b-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="3126b-108">Bir işlev çağrısının döndürme değeri hakkında bilgi sağlayan bir "ICorDebugValue" arabirim nesnesinin adresine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3126b-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3126b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3126b-109">Remarks</span></span>  
 <span data-ttu-id="3126b-110">Bu yöntem ile birlikte kullanılan [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir yöntemin dönüş değerini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3126b-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="3126b-111">Dönüş değerleri, aşağıdaki iki kod örneği gibi yöntemler özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="3126b-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="3126b-112">İlk örneği çağrıları <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemi, ancak yöntemin dönüş değerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="3126b-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="3126b-113">İkinci örnek hata ayıklamada çok daha yaygın bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3126b-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="3126b-114">Bir yöntem, yöntem çağrısında bağımsız değişken olarak kullanıldığından dönüş değeri, yalnızca hata ayıklayıcı çağrılan yöntem üzerinden adımları olduğunda da erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3126b-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="3126b-115">Özellikle çağrılan yöntem bir harici kitaplık olarak tanımlandığında çoğu durumda, mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="3126b-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="3126b-116">Geçirirseniz [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) bir işlev çağrısı siteye IL uzaklığı bir yöntemi, bir veya daha fazla yerel uzaklıklar verir.</span><span class="sxs-lookup"><span data-stu-id="3126b-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="3126b-117">Hata ayıklayıcı, ardından işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3126b-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="3126b-118">Hata ayıklayıcı kesme noktalarından birine eriştiğinde, dönüş değeri almak için bu yönteme geçilen aynı IL uzaklığını geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3126b-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="3126b-119">Ardından hata ayıklayıcıyı ayarladığı tüm kesme noktalarını temizlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3126b-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3126b-120">[Icordebugcode3::getreturnvalueliveoffset metodu](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3126b-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="3126b-121">Değer türlerinden dönüş değeri bilgilerini alma (diğer bir deyişle, öğesinden türetilen tüm türler <xref:System.ValueType>) desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3126b-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="3126b-122">Tarafından belirtilen IL uzaklığı `ILOffset` parametresi bir işlev çağrısı sitesinde olmalıdır ve hata ayıklanan adresindeki tarafından döndürülen yerel uzaklıkta ayarlanan bir kesme noktasında durdurulmalıdır [Icordebugcode3::getreturnvalueliveoffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi aynı IL uzaklığı için.</span><span class="sxs-lookup"><span data-stu-id="3126b-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="3126b-123">Hata ayıklanan belirtilen IL uzaklığı için doğru konumda durdurulmamışsa API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3126b-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="3126b-124">İşlev çağrısı bir değer döndürmezse API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3126b-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="3126b-125">`ICorDebugILFrame3::GetReturnValueForILOffset` Yöntemi yalnızca x86 tabanlı üzerinde kullanılabilir ve AMD64 sistemlerinde.</span><span class="sxs-lookup"><span data-stu-id="3126b-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3126b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3126b-126">Requirements</span></span>  
 <span data-ttu-id="3126b-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3126b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3126b-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3126b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3126b-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3126b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3126b-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3126b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3126b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3126b-131">See also</span></span>

- [<span data-ttu-id="3126b-132">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3126b-132">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="3126b-133">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3126b-133">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
