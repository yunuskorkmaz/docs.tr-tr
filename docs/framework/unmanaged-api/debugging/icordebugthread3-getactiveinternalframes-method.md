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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178460"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="5cf4b-102">ICorDebugThread3::GetActiveInternalFrames Metodu</span><span class="sxs-lookup"><span data-stu-id="5cf4b-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="5cf4b-103">Yığında bir dizi iç çerçeve[(ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cf4b-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cf4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cf4b-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="5cf4b-106">[içinde] 'de `ppInternalFrames`beklenen iç çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="5cf4b-107">[çıkış] Yığındaki iç `ULONG32` çerçeve sayısını içeren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="5cf4b-108">[içinde, dışarı] Yığındaki bir iç çerçeve dizisinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cf4b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5cf4b-109">Return Value</span></span>  
 <span data-ttu-id="5cf4b-110">Bu yöntem, yöntem hatasını gösteren HRESULT hatalarının yanı sıra aşağıdaki özel HRESULT'ları da döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5cf4b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cf4b-111">HRESULT</span></span>|<span data-ttu-id="5cf4b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cf4b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cf4b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cf4b-113">S_OK</span></span>|<span data-ttu-id="5cf4b-114">[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesnesi başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="5cf4b-115">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="5cf4b-115">E_INVALIDARG</span></span>|<span data-ttu-id="5cf4b-116">`cInternalFrames`sıfır değildir `ppInternalFrames` ve `null`, `pcInternalFrames` `null`ya da .</span><span class="sxs-lookup"><span data-stu-id="5cf4b-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="5cf4b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="5cf4b-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="5cf4b-118">`ppInternalFrames`iç çerçeve sayısından daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="5cf4b-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5cf4b-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cf4b-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cf4b-120">Remarks</span></span>  
 <span data-ttu-id="5cf4b-121">İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına itilen veri yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="5cf4b-122">İlk aradığınızda, `GetActiveInternalFrames`parametreyi `cInternalFrames` 0 (sıfır) ve `ppInternalFrames` parametreyi null olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="5cf4b-123">İlk `GetActiveInternalFrames` döndürdüğünde, `pcInternalFrames` yığındaki iç çerçevesayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="5cf4b-124">`GetActiveInternalFrames`sonra ikinci kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="5cf4b-125">Parametredeki uygun sayıyı (`pcInternalFrames`) geçirmeli ve 'de `ppInternalFrames`uygun büyüklükteki bir diziye işaretçi belirtmelisiniz. `cInternalFrames`</span><span class="sxs-lookup"><span data-stu-id="5cf4b-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="5cf4b-126">Gerçek yığın çerçevelerini döndürmek için [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cf4b-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cf4b-127">Requirements</span></span>  
 <span data-ttu-id="5cf4b-128">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cf4b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cf4b-129">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cf4b-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cf4b-130">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cf4b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cf4b-131">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf4b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf4b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-132">See also</span></span>

- [<span data-ttu-id="5cf4b-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5cf4b-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5cf4b-134">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5cf4b-134">Debugging</span></span>](index.md)
