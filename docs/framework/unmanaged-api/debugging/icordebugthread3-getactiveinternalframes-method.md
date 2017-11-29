---
title: ICorDebugThread3::GetActiveInternalFrames Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.GetActiveInternalFrames Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b94827ac49c69c5e72c2e300a80914774cc498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="1fa87-102">ICorDebugThread3::GetActiveInternalFrames Metodu</span><span class="sxs-lookup"><span data-stu-id="1fa87-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="1fa87-103">İç çerçeveleri bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneler) yığında.</span><span class="sxs-lookup"><span data-stu-id="1fa87-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fa87-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fa87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fa87-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="1fa87-106">[in] Beklenen iç çerçeve sayısı `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="1fa87-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="1fa87-107">[out] Bir işaretçi bir `ULONG32` yığında iç çerçeve sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="1fa87-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="1fa87-108">[içinde out] Yığında iç çerçeveler dizisi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1fa87-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fa87-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1fa87-109">Return Value</span></span>  
 <span data-ttu-id="1fa87-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="1fa87-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1fa87-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1fa87-111">HRESULT</span></span>|<span data-ttu-id="1fa87-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fa87-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fa87-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fa87-113">S_OK</span></span>|<span data-ttu-id="1fa87-114">[Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1fa87-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="1fa87-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1fa87-115">E_INVALIDARG</span></span>|<span data-ttu-id="1fa87-116">`cInternalFrames`sıfır değil ve `ppInternalFrames` olan `null`, veya `pcInternalFrames` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="1fa87-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="1fa87-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="1fa87-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="1fa87-118">`ppInternalFrames`İç çerçeveler sayısından daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="1fa87-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1fa87-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="1fa87-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fa87-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fa87-120">Remarks</span></span>  
 <span data-ttu-id="1fa87-121">İç çerçeveler yığına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını ' dir.</span><span class="sxs-lookup"><span data-stu-id="1fa87-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="1fa87-122">İlk çağırdığınızda `GetActiveInternalFrames`, ayarlamanız gerekir `cInternalFrames` parametresi 0 (sıfır) ve `ppInternalFrames` parametresi null.</span><span class="sxs-lookup"><span data-stu-id="1fa87-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="1fa87-123">Zaman `GetActiveInternalFrames` ilk döndürür, `pcInternalFrames` yığında iç çerçeve sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="1fa87-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="1fa87-124">`GetActiveInternalFrames`ardından ikinci bir kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fa87-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="1fa87-125">Uygun sayısı geçirmelisiniz (`pcInternalFrames`) içinde `cInternalFrames` parametresi ve uygun şekilde boyutlu bir dizide bir işaretçi belirtin `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="1fa87-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="1fa87-126">Kullanım [Icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) gerçek döndürülecek yöntemi yığın çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="1fa87-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fa87-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fa87-127">Requirements</span></span>  
 <span data-ttu-id="1fa87-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fa87-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa87-129">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fa87-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fa87-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fa87-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fa87-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fa87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa87-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fa87-132">See Also</span></span>  
 [<span data-ttu-id="1fa87-133">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1fa87-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1fa87-134">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1fa87-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
