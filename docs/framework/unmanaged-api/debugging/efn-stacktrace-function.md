---
title: "_EFN_StackTrace İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 905a44ee3187bc920d9342b043383a1500c28985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="dd603-102">_EFN_StackTrace İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd603-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="dd603-103">Yönetilen yığın izlemesi metin gösterimini ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.</span><span class="sxs-lookup"><span data-stu-id="dd603-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd603-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd603-104">Syntax</span></span>  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd603-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd603-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="dd603-106">[in] Ayıklanacak istemci.</span><span class="sxs-lookup"><span data-stu-id="dd603-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="dd603-107">[out] Yığın izleme metin gösterimi.</span><span class="sxs-lookup"><span data-stu-id="dd603-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="dd603-108">[out] Karakter sayısını gösteren bir işaretçi `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="dd603-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="dd603-109">[out] Geçişi içerikleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="dd603-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="dd603-110">[out] Geçişi içerikleri dizisindeki sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dd603-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="dd603-111">[in] Bağlam yapısı boyutu.</span><span class="sxs-lookup"><span data-stu-id="dd603-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="dd603-112">[in] EBP kayıt ve her önünde enter yığın işaretçisi (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlayın `module!functionname` satır.</span><span class="sxs-lookup"><span data-stu-id="dd603-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd603-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd603-113">Remarks</span></span>  
 <span data-ttu-id="dd603-114">`_EFN_StackTrace` Yapısı WinDbg programlı arabiriminden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd603-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="dd603-115">Parametreleri aşağıdaki gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="dd603-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="dd603-116">Varsa `wszTextOut` null ve `puiTextLength` olan null, işlev dize uzunluğunu döndürür `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="dd603-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="dd603-117">Varsa `wszTextOut` olan null, işlev metinde depolar `wszTextOut` tarafından belirtilen konumda kadar `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="dd603-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="dd603-118">Başarıyla arabellek yeterince uzun değildi, arabellek ya da döndürür E_OUTOFMEMORY yeterli alan olduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd603-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="dd603-119">İşlev geçiş kısmı yoksayılır `pTransitionContexts` ve `puiTransitionContextCount` her ikisi de null olan.</span><span class="sxs-lookup"><span data-stu-id="dd603-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="dd603-120">Bu durumda, yalnızca işlev adlarını metin çıktısını ile arayanlar işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd603-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="dd603-121">Varsa `pTransitionContexts` null ve `puiTransitionContextCount` olan null, işlevi gerekli sayısı bağlam giriş döndürür `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="dd603-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="dd603-122">Varsa `pTransitionContexts` olan null, işlevi ona yapıları uzunlukta bir dizi gibi davranır `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="dd603-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="dd603-123">Yapı boyutu tarafından verilen `uiSizeOfContext`, ve boyutunu olmalıdır [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) veya `CONTEXT` mimarisi için.</span><span class="sxs-lookup"><span data-stu-id="dd603-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="dd603-124">`wszTextOut`şu biçimde yazılır:</span><span class="sxs-lookup"><span data-stu-id="dd603-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="dd603-125">Onaltılık uzaklık 0x0 ise, uzaklık yazılır.</span><span class="sxs-lookup"><span data-stu-id="dd603-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="dd603-126">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd603-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="dd603-127">`Flags` Parametredir 0 veya EBP ve ESP her önünde görmek için SOS_STACKTRACE_SHOWADDRESSES `module!functionname` satır.</span><span class="sxs-lookup"><span data-stu-id="dd603-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="dd603-128">Varsayılan olarak, 0'dır.</span><span class="sxs-lookup"><span data-stu-id="dd603-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="dd603-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd603-129">Requirements</span></span>  
 <span data-ttu-id="dd603-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd603-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd603-131">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="dd603-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="dd603-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd603-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd603-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd603-133">See Also</span></span>  
 [<span data-ttu-id="dd603-134">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dd603-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
