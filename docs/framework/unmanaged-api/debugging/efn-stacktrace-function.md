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
ms.openlocfilehash: 9b7624c2902d17e437cda9a0a84ddf288323b577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676198"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="0b1df-102">\_EFN \_ StackTrace işlevi</span><span class="sxs-lookup"><span data-stu-id="0b1df-102">\_EFN\_StackTrace Function</span></span>

<span data-ttu-id="0b1df-103">`CONTEXT`Yönetilmeyen ve yönetilen kod arasındaki her geçiş için bir yönetilen yığın izlemenin ve bir kayıt dizisinin metin gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b1df-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1df-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0b1df-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="0b1df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b1df-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="0b1df-106">'ndaki Hata ayıklamakta olan istemci.</span><span class="sxs-lookup"><span data-stu-id="0b1df-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="0b1df-107">dışı Yığın izlemenin metin temsili.</span><span class="sxs-lookup"><span data-stu-id="0b1df-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="0b1df-108">dışı İçindeki karakter sayısına yönelik bir işaretçi `wszTextOut` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="0b1df-109">dışı Geçiş bağlamlarının dizisi.</span><span class="sxs-lookup"><span data-stu-id="0b1df-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="0b1df-110">dışı Dizideki geçiş bağlamlarının sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b1df-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="0b1df-111">'ndaki Bağlam yapısının boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b1df-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="0b1df-112">'ndaki Her satırın önünde EBP kaydını ve ENTER yığın işaretçisini (ESP) göstermek için 0 veya SOS_STACKTRACE_SHOWADDRESSES (0x01) olarak ayarlayın `module!functionname` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b1df-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b1df-113">Remarks</span></span>  

 <span data-ttu-id="0b1df-114">`_EFN_StackTrace`Yapı bir WinDbg programlı arabiriminden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b1df-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="0b1df-115">Parametreleri aşağıdaki gibi kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0b1df-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="0b1df-116">`wszTextOut`Null ise ve `puiTextLength` null değilse, işlev içindeki dize uzunluğunu döndürür `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="0b1df-117">`wszTextOut`Null değilse, işlev `wszTextOut` tarafından belirtilen konuma kadar metni depolar `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="0b1df-118">Arabellekte yeterli yer varsa başarıyla geri döner veya arabellek yeterince uzunsa E_OUTOFMEMORY döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b1df-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="0b1df-119">İşlevin geçiş bölümü, `pTransitionContexts` ve `puiTransitionContextCount` her ikisi de null ise yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0b1df-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="0b1df-120">Bu durumda, işlev çağıranları yalnızca işlev adlarının metin çıktısı ile birlikte sunar.</span><span class="sxs-lookup"><span data-stu-id="0b1df-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="0b1df-121">`pTransitionContexts`Null ise ve `puiTransitionContextCount` null değilse, işlev içinde gereken bağlam girişi sayısını döndürür `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="0b1df-122">`pTransitionContexts`Null değilse, işlev bunu bir dizi yapının dizisi olarak değerlendirir `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="0b1df-123">Yapı boyutu tarafından verilir `uiSizeOfContext` ve [SimpleContext](stacktrace-simplecontext-structure.md) 'in veya `CONTEXT` mimarinin boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b1df-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="0b1df-124">`wszTextOut` aşağıdaki biçimde yazılır:</span><span class="sxs-lookup"><span data-stu-id="0b1df-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="0b1df-125">Onaltılı konum 0x0 ise, hiçbir fark yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="0b1df-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="0b1df-126">Şu anda bağlamda olan iş parçacığında yönetilen kod yoksa, işlev SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b1df-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="0b1df-127">`Flags`Her satırın önünde EBP ve ESP görmek için parametresi 0 veya SOS_STACKTRACE_SHOWADDRESSES `module!functionname` .</span><span class="sxs-lookup"><span data-stu-id="0b1df-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="0b1df-128">Varsayılan olarak, 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="0b1df-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="0b1df-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b1df-129">Requirements</span></span>  

 <span data-ttu-id="0b1df-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b1df-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b1df-131">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="0b1df-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0b1df-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b1df-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1df-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b1df-133">See also</span></span>

- [<span data-ttu-id="0b1df-134">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0b1df-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
