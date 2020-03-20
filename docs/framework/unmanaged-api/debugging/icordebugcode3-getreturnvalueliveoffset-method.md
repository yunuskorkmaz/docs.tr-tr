---
title: ICorDebugCode3::GetReturnValueLiveOffset Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178948"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="3fb5e-102">ICorDebugCode3::GetReturnValueLiveOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="3fb5e-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="3fb5e-103">Belirli bir IL ofset için, hata ayıklamanın bir işlevden geri dönüş değerini elde edilebilmek için kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fb5e-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fb5e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fb5e-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="3fb5e-106">IL ofset.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-106">The IL offset.</span></span> <span data-ttu-id="3fb5e-107">Bir işlev arama sitesi olmalıdır veya işlev çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="3fb5e-108">Depolamak `pOffsets`için kullanılabilir bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="3fb5e-109">Geri döndürülen uzaklık sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="3fb5e-110">Genellikle değeri 1'dir, ancak tek bir IL `CALL` yönergesi birden çok montaj yönergesi ile eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="3fb5e-111">Bir dizi yerel uzaklık.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-111">An array of native offsets.</span></span> <span data-ttu-id="3fb5e-112">Tipik olarak, tek bir IL yönergesi birden çok `CALL` derleme yönergesi için birden çok harita eşleyebilir rağmen, `pOffsets` tek bir ofset içerir.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb5e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fb5e-113">Remarks</span></span>  
 <span data-ttu-id="3fb5e-114">Bu yöntem, başvuru türünü döndüren bir yöntemin geri dönüş değerini almak için [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemi ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="3fb5e-115">Bir IŞLEV çağrı sitesine IL ofset'in bu yönteme geçirilmesi bir veya daha fazla yerel uzaklık döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="3fb5e-116">Hata ayıklama, işlevdeki bu yerel uzaklıklarda kesme noktaları ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="3fb5e-117">Hata ayıklayıcı kesme noktalarından birine ulaştığında, bu yönteme geçtiğiniz IL ofsetini iade değerini almak için [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="3fb5e-118">Hata ayıklama daha sonra ayarladığının tüm kesme noktalarını temizlemelidir.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="3fb5e-119">`ICorDebugCode3::GetReturnValueLiveOffset` Ve [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemleri yalnızca başvuru türleri için iade değeri bilgileri almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="3fb5e-120">İade değeri bilgilerinin değer türlerinden (diğer bir şekilde) <xref:System.ValueType>alınması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="3fb5e-121">İşlev aşağıdaki `HRESULT` tabloda gösterilen değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="3fb5e-122">`HRESULT`Değer</span><span class="sxs-lookup"><span data-stu-id="3fb5e-122">`HRESULT` value</span></span>|<span data-ttu-id="3fb5e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fb5e-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="3fb5e-124">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="3fb5e-125">Verilen IL ofset sitesi bir çağrı yönergesi değildir veya işlev döndürür. `void`</span><span class="sxs-lookup"><span data-stu-id="3fb5e-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="3fb5e-126">Verilen IL ofset uygun bir çağrıdır, ancak iade türü iade değeri almak için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="3fb5e-127">Bu `ICorDebugCode3::GetReturnValueLiveOffset` yöntem yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb5e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fb5e-128">Requirements</span></span>  
 <span data-ttu-id="3fb5e-129">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb5e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb5e-130">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fb5e-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fb5e-131">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fb5e-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb5e-132">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb5e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb5e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb5e-133">See also</span></span>

- [<span data-ttu-id="3fb5e-134">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3fb5e-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="3fb5e-135">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fb5e-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
