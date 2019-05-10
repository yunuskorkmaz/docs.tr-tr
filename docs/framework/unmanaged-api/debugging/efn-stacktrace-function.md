---
title: _EFN_StackTrace İşlevi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0074584ee5baba358db5bf3b0f2cfdd9a3d8f1d9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593533"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="6424f-102">_EFN_StackTrace İşlevi</span><span class="sxs-lookup"><span data-stu-id="6424f-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="6424f-103">Yönetilen yığın izlemesi metin gösterimi ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.</span><span class="sxs-lookup"><span data-stu-id="6424f-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6424f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6424f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6424f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6424f-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="6424f-106">[in] Hatası ayıklanmakta olan istemci.</span><span class="sxs-lookup"><span data-stu-id="6424f-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="6424f-107">[out] Yığın izlemesi metin gösterimi.</span><span class="sxs-lookup"><span data-stu-id="6424f-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="6424f-108">[out] Karakter sayısı için bir işaretçi `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="6424f-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="6424f-109">[out] Geçiş bağlamları dizisi.</span><span class="sxs-lookup"><span data-stu-id="6424f-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="6424f-110">[out] Dizi bağlamlarda geçiş sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6424f-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="6424f-111">[in] Context yapısını boyutu.</span><span class="sxs-lookup"><span data-stu-id="6424f-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="6424f-112">[in] EBP kayıt ve her önüne enter yığın işaretçisi (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlanmış `module!functionname` satır.</span><span class="sxs-lookup"><span data-stu-id="6424f-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6424f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6424f-113">Remarks</span></span>  
 <span data-ttu-id="6424f-114">`_EFN_StackTrace` Yapısı WinDbg programlı arabiriminden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6424f-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="6424f-115">Parametreler şu şekilde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6424f-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="6424f-116">Varsa `wszTextOut` null ve `puiTextLength` olduğu null, işlev dize uzunluğunu döndürür `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="6424f-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="6424f-117">Varsa `wszTextOut` olan metin null, işlev depolar `wszTextOut` tarafından belirtilen konum kadar `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="6424f-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="6424f-118">Başarıyla arabellek yeterince uzun değildi, arabellek veya E_OUTOFMEMORY döndürür içinde yeterli yer olduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6424f-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="6424f-119">İşlev geçişi kısmı yoksayılır `pTransitionContexts` ve `puiTransitionContextCount` her ikisi de null olan.</span><span class="sxs-lookup"><span data-stu-id="6424f-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="6424f-120">Bu durumda, yalnızca işlev adlarını metin çıktısı ile çağıranlar işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6424f-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="6424f-121">Varsa `pTransitionContexts` null ve `puiTransitionContextCount` olduğu null, işlev bağlam girişler gerekli sayısını döndürür `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="6424f-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="6424f-122">Varsa `pTransitionContexts` olduğu null, işlevi, yapıları uzunlukta bir dizi gibi davranır `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="6424f-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="6424f-123">Yapı boyutu tarafından verilen `uiSizeOfContext`, ve boyutunu olmalıdır [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) veya `CONTEXT` mimarisi.</span><span class="sxs-lookup"><span data-stu-id="6424f-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="6424f-124">`wszTextOut` şu biçimde yazılır:</span><span class="sxs-lookup"><span data-stu-id="6424f-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="6424f-125">Onaltılık uzaklık 0x0 ise, hiçbir uzaklığı yazılır.</span><span class="sxs-lookup"><span data-stu-id="6424f-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="6424f-126">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6424f-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="6424f-127">`Flags` Parametresi, 0 veya EBP ve ESP her önüne görmek için SOS_STACKTRACE_SHOWADDRESSES `module!functionname` satır.</span><span class="sxs-lookup"><span data-stu-id="6424f-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="6424f-128">Varsayılan olarak, 0'dır.</span><span class="sxs-lookup"><span data-stu-id="6424f-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="6424f-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6424f-129">Requirements</span></span>  
 <span data-ttu-id="6424f-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6424f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6424f-131">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="6424f-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6424f-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6424f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6424f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6424f-133">See also</span></span>

- [<span data-ttu-id="6424f-134">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6424f-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
