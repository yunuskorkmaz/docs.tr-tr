---
title: 'ICorDebugVirtualUnwinder:: Next yöntemi'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967929"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="76f4d-102">ICorDebugVirtualUnwinder:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="76f4d-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="76f4d-103">Çağıranın bağlamına ilerletir.</span><span class="sxs-lookup"><span data-stu-id="76f4d-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76f4d-105">Parameters</span></span>  
 <span data-ttu-id="76f4d-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="76f4d-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76f4d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76f4d-107">Return Value</span></span>  
 <span data-ttu-id="76f4d-108">`S_OK`geriye doğru izleme işlemi başarılı olduysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru tamamlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="76f4d-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="76f4d-109">Başarısız bir HRESULT döndürülürse, ICorDebug API 'Leri `CORDBG_E_DATA_TARGET_ERROR`döndürülür.</span><span class="sxs-lookup"><span data-stu-id="76f4d-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76f4d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76f4d-110">Remarks</span></span>  
 <span data-ttu-id="76f4d-111">Yığın denetçisi ilerlemeye devam ettiğinden emin olunması gerekir, bu yüzden bir çağrısının `Next` başarısız bir HRESULT veya `CORDBG_S_AT_END_OF_STACK`geri dönmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="76f4d-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="76f4d-112">Süresiz `S_OK` olarak döndürmek sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="76f4d-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76f4d-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76f4d-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f4d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76f4d-114">Requirements</span></span>  
 <span data-ttu-id="76f4d-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f4d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f4d-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76f4d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76f4d-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76f4d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f4d-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f4d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f4d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76f4d-119">See also</span></span>

- [<span data-ttu-id="76f4d-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76f4d-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="76f4d-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76f4d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
