---
title: ICorDebugNativeFrame2::GetStackParameterSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4baa58159760af12afca5b84cb6b1b66e46093
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485544"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="bb569-102">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb569-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="bb569-103">İşletim sistemlerini x86 yığındaki parametreleri toplam boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb569-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb569-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb569-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb569-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb569-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="bb569-106">[out] Toplam boyutu, yığındaki parametreleri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb569-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb569-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb569-107">Return Value</span></span>  
 <span data-ttu-id="bb569-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="bb569-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb569-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb569-109">HRESULT</span></span>|<span data-ttu-id="bb569-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb569-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb569-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb569-111">S_OK</span></span>|<span data-ttu-id="bb569-112">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bb569-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="bb569-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bb569-113">S_FALSE</span></span>|<span data-ttu-id="bb569-114">`GetStackParameterSize` x86 olmayan platformunda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="bb569-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="bb569-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb569-115">E_FAIL</span></span>|<span data-ttu-id="bb569-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="bb569-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="bb569-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bb569-117">E_INVALIDARG</span></span>|<span data-ttu-id="bb569-118">`pSize` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="bb569-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bb569-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="bb569-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb569-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb569-120">Remarks</span></span>  
 <span data-ttu-id="bb569-121">[Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yöntemleri yığına itildi parametreleri için yığın işaretçisi ayarlama değil.</span><span class="sxs-lookup"><span data-stu-id="bb569-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="bb569-122">Tarafından döndürülen değeri, bunun yerine kullanabileceğiniz `GetStackParameterSize` parametrelerini ayarla bir yerel unwinder sağlamak için yığın işaretçisi ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="bb569-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb569-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb569-123">Requirements</span></span>  
 <span data-ttu-id="bb569-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb569-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb569-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb569-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb569-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb569-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb569-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb569-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb569-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb569-128">See also</span></span>
- [<span data-ttu-id="bb569-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb569-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="bb569-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb569-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bb569-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bb569-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
