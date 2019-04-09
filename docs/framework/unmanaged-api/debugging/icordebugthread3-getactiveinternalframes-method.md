---
title: ICorDebugThread3::GetActiveInternalFrames Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e264f2361c739536d15fbf31d366db74e107bac2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085109"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="8bc2c-102">ICorDebugThread3::GetActiveInternalFrames Metodu</span><span class="sxs-lookup"><span data-stu-id="8bc2c-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="8bc2c-103">İç çerçeveler bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) yığında.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bc2c-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bc2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bc2c-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="8bc2c-106">[in] Beklenen iç çerçeve sayısı `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="8bc2c-107">[out] Bir işaretçi bir `ULONG32` içeren yığında iç çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="8bc2c-108">[out içinde] İç çerçeveler yığın üzerinde bir dizi adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc2c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8bc2c-109">Return Value</span></span>  
 <span data-ttu-id="8bc2c-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8bc2c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bc2c-111">HRESULT</span></span>|<span data-ttu-id="8bc2c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bc2c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bc2c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bc2c-113">S_OK</span></span>|<span data-ttu-id="8bc2c-114">[Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesne başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="8bc2c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8bc2c-115">E_INVALIDARG</span></span>|`cInternalFrames` <span data-ttu-id="8bc2c-116">sıfır değilse ve `ppInternalFrames` olduğu `null`, veya `pcInternalFrames` olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-116">is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="8bc2c-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="8bc2c-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|`ppInternalFrames` <span data-ttu-id="8bc2c-118">İç çerçeveler sayısından küçük.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-118">is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8bc2c-119">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8bc2c-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bc2c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bc2c-120">Remarks</span></span>  
 <span data-ttu-id="8bc2c-121">İç çerçeveler, yığın üstüne, geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="8bc2c-122">İlk çağırdığınızda `GetActiveInternalFrames`, ayarlamalısınız `cInternalFrames` parametresi 0 (sıfır) ve `ppInternalFrames` parametresi null.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="8bc2c-123">Zaman `GetActiveInternalFrames` ilk döndürür, `pcInternalFrames` yığında iç çerçeve sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 `GetActiveInternalFrames` <span data-ttu-id="8bc2c-124">ardından ikinci bir kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-124">should then be called a second time.</span></span> <span data-ttu-id="8bc2c-125">Uygun sayısı geçmelidir (`pcInternalFrames`) içinde `cInternalFrames` parametresi ve uygun boyutlandırılmış bir dizide bir işaretçi belirtin `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="8bc2c-126">Kullanım [Icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) gerçek döndürmek için yöntemin yığın çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc2c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bc2c-127">Requirements</span></span>  
 <span data-ttu-id="8bc2c-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bc2c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bc2c-129">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bc2c-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bc2c-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bc2c-130">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8bc2c-131">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8bc2c-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8bc2c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bc2c-132">See also</span></span>

- [<span data-ttu-id="8bc2c-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8bc2c-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8bc2c-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8bc2c-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
