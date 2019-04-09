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
ms.openlocfilehash: 47968d7550c3d16d201680caab705c0d7c85c784
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200148"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="bc949-102">ICorDebugNativeFrame2::GetStackParameterSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc949-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="bc949-103">İşletim sistemlerini x86 yığındaki parametreleri toplam boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc949-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc949-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc949-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc949-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc949-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="bc949-106">[out] Toplam boyutu, yığındaki parametreleri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc949-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc949-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc949-107">Return Value</span></span>  
 <span data-ttu-id="bc949-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="bc949-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bc949-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc949-109">HRESULT</span></span>|<span data-ttu-id="bc949-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc949-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc949-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc949-111">S_OK</span></span>|<span data-ttu-id="bc949-112">Yığın boyutu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bc949-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="bc949-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bc949-113">S_FALSE</span></span>|`GetStackParameterSize` <span data-ttu-id="bc949-114">x86 olmayan platformunda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="bc949-114">was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="bc949-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc949-115">E_FAIL</span></span>|`The size of the parameters could not be returned`<span data-ttu-id="bc949-116">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="bc949-116">.</span></span>|  
|<span data-ttu-id="bc949-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bc949-117">E_INVALIDARG</span></span>|`pSize` <span data-ttu-id="bc949-118">olan `null`.</span><span class="sxs-lookup"><span data-stu-id="bc949-118">Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bc949-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="bc949-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc949-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc949-120">Remarks</span></span>  
 <span data-ttu-id="bc949-121">[Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yöntemleri yığına itildi parametreleri için yığın işaretçisi ayarlama değil.</span><span class="sxs-lookup"><span data-stu-id="bc949-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="bc949-122">Tarafından döndürülen değeri, bunun yerine kullanabileceğiniz `GetStackParameterSize` parametrelerini ayarla bir yerel unwinder sağlamak için yığın işaretçisi ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="bc949-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc949-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc949-123">Requirements</span></span>  
 <span data-ttu-id="bc949-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc949-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc949-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc949-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc949-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc949-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bc949-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bc949-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bc949-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc949-128">See also</span></span>

- [<span data-ttu-id="bc949-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc949-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="bc949-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bc949-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bc949-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bc949-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
