---
title: "ICorDebugVirtualUnwinder::Next yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4dc0b8bf7915fe579c4764bc06c1f2534eeb759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="540be-102">ICorDebugVirtualUnwinder::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="540be-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="540be-103">Çağıranın içeriği ilerler.</span><span class="sxs-lookup"><span data-stu-id="540be-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="540be-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="540be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="540be-105">Parameters</span></span>  
 <span data-ttu-id="540be-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="540be-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="540be-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="540be-107">Return Value</span></span>  
 <span data-ttu-id="540be-108">`S_OK`bırakma başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve yok olduğundan bırakma tamamlanamazsa.</span><span class="sxs-lookup"><span data-stu-id="540be-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="540be-109">Döndürülen HRESULT başarısız, Icordebug API'leri döndürür, `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="540be-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="540be-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="540be-110">Remarks</span></span>  
 <span data-ttu-id="540be-111">Yığın walker, ilerleme, sonuç olarak bu kılar emin olmalısınız yapılan bir çağrı `Next` başarısız döndürülecek HRESULT veya `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="540be-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="540be-112">Döndürme `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="540be-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="540be-113">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="540be-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="540be-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="540be-114">Requirements</span></span>  
 <span data-ttu-id="540be-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="540be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="540be-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="540be-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="540be-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="540be-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="540be-118">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="540be-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540be-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="540be-119">See Also</span></span>  
 [<span data-ttu-id="540be-120">ICorDebugMemoryBuffer arabirimi</span><span class="sxs-lookup"><span data-stu-id="540be-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="540be-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="540be-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
