---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugCode3:: Getreturnvaluelivesapmasını yöntemi'
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
ms.openlocfilehash: 6ec9a342805c047d7331c3ce2af2a4ffba596a26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711017"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="e7425-103">ICorDebugCode3::GetReturnValueLiveOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="e7425-103">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>

<span data-ttu-id="e7425-104">Belirtilen bir Il ofseti için, hata ayıklayıcının bir işlevden dönüş değeri alabileceği şekilde, bir kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="e7425-104">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7425-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7425-105">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7425-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7425-106">Parameters</span></span>  

 `ILoffset`  
 <span data-ttu-id="e7425-107">Il kayması.</span><span class="sxs-lookup"><span data-stu-id="e7425-107">The IL offset.</span></span> <span data-ttu-id="e7425-108">İşlevin çağrı sitesi olması gerekir veya işlev çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e7425-108">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="e7425-109">Depolanacak kullanılabilir bayt sayısı `pOffsets` .</span><span class="sxs-lookup"><span data-stu-id="e7425-109">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="e7425-110">Gerçekten döndürülen uzaklık sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7425-110">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="e7425-111">Genellikle değeri 1 ' dir, ancak tek bir Il yönergesi birden çok `CALL` derleme yönergesiyle eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7425-111">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="e7425-112">Yerel uzaklık dizisi.</span><span class="sxs-lookup"><span data-stu-id="e7425-112">An array of native offsets.</span></span> <span data-ttu-id="e7425-113">Genellikle, tek `pOffsets` bir konum içerir, ancak tek BIR Il yönergesi birden çok `CALL` derleme yönergesiyle birden çok haritaya eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e7425-113">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7425-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7425-114">Remarks</span></span>  

 <span data-ttu-id="e7425-115">Bu yöntem, başvuru türü döndüren bir yöntemin dönüş değerini almak için [ICorDebugILFrame3:: Getreturnvalueforılsapmasını](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemi ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7425-115">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="e7425-116">Bir işlev çağrısı sitesine bir Il uzaklığının bu yönteme geçirilmesi bir veya daha fazla yerel uzaklık döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7425-116">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="e7425-117">Hata ayıklayıcı daha sonra işlevdeki bu yerel kaydırmalar üzerinde kesme noktaları ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e7425-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="e7425-118">Hata ayıklayıcı kesme noktalarından birine geçtiğinde, dönüş değerini almak için bu yönteme geçirdiğiniz Il sapmasını [ICorDebugILFrame3:: Getreturnvalueforılsapmasını](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemine geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7425-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="e7425-119">Hata ayıklayıcı daha sonra, ayarlandığı tüm kesme noktalarını temizlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e7425-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e7425-120">`ICorDebugCode3::GetReturnValueLiveOffset`Ve [ICorDebugILFrame3:: Getreturnvalueforılsapmasını](icordebugilframe3-getreturnvalueforiloffset-method.md) yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7425-120">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="e7425-121">Değer türlerinden dönüş değeri bilgileri alma (yani, öğesinden türetilen tüm türler <xref:System.ValueType> ) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e7425-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="e7425-122">İşlevi, `HRESULT` Aşağıdaki tabloda gösterilen değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7425-122">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="e7425-123">`HRESULT` deeri</span><span class="sxs-lookup"><span data-stu-id="e7425-123">`HRESULT` value</span></span>|<span data-ttu-id="e7425-124">Description</span><span class="sxs-lookup"><span data-stu-id="e7425-124">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="e7425-125">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="e7425-125">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="e7425-126">Verilen Il konum sitesi bir çağrı yönergesi değil veya işlev döndürüyor `void` .</span><span class="sxs-lookup"><span data-stu-id="e7425-126">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="e7425-127">Verilen Il kayması uygun bir çağrıdır, ancak dönüş türü bir dönüş değeri almak için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e7425-127">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="e7425-128">`ICorDebugCode3::GetReturnValueLiveOffset`Yöntemi yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7425-128">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7425-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7425-129">Requirements</span></span>  

 <span data-ttu-id="e7425-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7425-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7425-131">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e7425-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7425-132">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e7425-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7425-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7425-133">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7425-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7425-134">See also</span></span>

- [<span data-ttu-id="e7425-135">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7425-135">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="e7425-136">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7425-136">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
