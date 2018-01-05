---
title: ICorDebugNativeFrame2::GetStackParameterSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="47893-102">ICorDebugNativeFrame2::GetStackParameterSize Metodu</span><span class="sxs-lookup"><span data-stu-id="47893-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="47893-103">İşletim sistemleri x86 yığında parametreleri toplam boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="47893-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47893-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47893-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47893-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47893-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="47893-106">[out] Yığın parametreleri toplam boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="47893-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47893-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47893-107">Return Value</span></span>  
 <span data-ttu-id="47893-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="47893-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47893-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47893-109">HRESULT</span></span>|<span data-ttu-id="47893-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47893-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47893-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="47893-111">S_OK</span></span>|<span data-ttu-id="47893-112">Yığın boyutunu başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="47893-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="47893-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="47893-113">S_FALSE</span></span>|<span data-ttu-id="47893-114">`GetStackParameterSize`x86 olmayan platformda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="47893-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="47893-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47893-115">E_FAIL</span></span>|<span data-ttu-id="47893-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="47893-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="47893-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="47893-117">E_INVALIDARG</span></span>|<span data-ttu-id="47893-118">`pSize`Olan `null`.</span><span class="sxs-lookup"><span data-stu-id="47893-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="47893-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="47893-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47893-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47893-120">Remarks</span></span>  
 <span data-ttu-id="47893-121">[Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yöntemleri yığına parametreler için yığın işaretçisi Ayarla değil.</span><span class="sxs-lookup"><span data-stu-id="47893-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="47893-122">Bunun yerine, tarafından döndürülen değer kullanabilirsiniz `GetStackParameterSize` parametrelerini ayarlamak bir yerel unwinder oluşturmak için yığın işaretçisi ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="47893-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47893-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47893-123">Requirements</span></span>  
 <span data-ttu-id="47893-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47893-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47893-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47893-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47893-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47893-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47893-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47893-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47893-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47893-128">See Also</span></span>  
 [<span data-ttu-id="47893-129">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47893-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="47893-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="47893-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="47893-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="47893-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
