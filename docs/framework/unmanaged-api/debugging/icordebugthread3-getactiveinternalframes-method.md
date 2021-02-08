---
description: 'Daha fazla bilgi edinin: ICorDebugThread3:: GetActiveInternalFrames yöntemi'
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
ms.openlocfilehash: f228dd84708478bb364ac09407a68df3e8d971b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800987"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="cb8bb-103">ICorDebugThread3::GetActiveInternalFrames Metodu</span><span class="sxs-lookup"><span data-stu-id="cb8bb-103">ICorDebugThread3::GetActiveInternalFrames Method</span></span>

<span data-ttu-id="cb8bb-104">Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-104">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb8bb-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb8bb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb8bb-106">Parameters</span></span>  

 `cInternalFrames`  
 <span data-ttu-id="cb8bb-107">'ndaki İçinde beklenen iç çerçeve sayısı `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="cb8bb-107">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="cb8bb-108">dışı `ULONG32` Yığın üzerindeki iç çerçevelerin sayısını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-108">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="cb8bb-109">[in, out] Yığındaki iç çerçeveler dizisinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-109">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb8bb-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb8bb-110">Return Value</span></span>  

 <span data-ttu-id="cb8bb-111">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cb8bb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb8bb-112">HRESULT</span></span>|<span data-ttu-id="cb8bb-113">Description</span><span class="sxs-lookup"><span data-stu-id="cb8bb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb8bb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb8bb-114">S_OK</span></span>|<span data-ttu-id="cb8bb-115">[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesnesi başarıyla oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-115">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="cb8bb-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cb8bb-116">E_INVALIDARG</span></span>|<span data-ttu-id="cb8bb-117">`cInternalFrames` sıfır değildir ve `ppInternalFrames` `null` , veya ' dir `pcInternalFrames` `null` .</span><span class="sxs-lookup"><span data-stu-id="cb8bb-117">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="cb8bb-118">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="cb8bb-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="cb8bb-119">`ppInternalFrames` , iç çerçeve sayısından daha küçüktür.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-119">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cb8bb-120">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="cb8bb-120">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb8bb-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb8bb-121">Remarks</span></span>  

 <span data-ttu-id="cb8bb-122">İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-122">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="cb8bb-123">İlk kez çağırdığınızda `GetActiveInternalFrames` `cInternalFrames` parametresini 0 (sıfır) ve parametresini null olarak ayarlamanız gerekir `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="cb8bb-123">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="cb8bb-124">`GetActiveInternalFrames`İlk döndüğünde, `pcInternalFrames` yığındaki iç çerçevelerin sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-124">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="cb8bb-125">`GetActiveInternalFrames` ikinci kez çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-125">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="cb8bb-126">Parametreye doğru Count ( `pcInternalFrames` ) geçirin `cInternalFrames` ve içinde uygun boyutta bir diziye yönelik bir işaretçi belirtmeniz gerekir `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="cb8bb-126">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="cb8bb-127">Gerçek yığın çerçevelerini döndürmek için [ıcordebugstackyürüme:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-127">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8bb-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb8bb-128">Requirements</span></span>  

 <span data-ttu-id="cb8bb-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb8bb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8bb-130">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb8bb-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb8bb-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb8bb-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb8bb-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb8bb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8bb-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb8bb-133">See also</span></span>

- [<span data-ttu-id="cb8bb-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cb8bb-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cb8bb-135">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cb8bb-135">Debugging</span></span>](index.md)
