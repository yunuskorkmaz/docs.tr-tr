---
title: ICorDebugVirtualUnwinder::Next yöntemi
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076893"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="518ef-102">ICorDebugVirtualUnwinder::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="518ef-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="518ef-103">Arayanın bağlam ilerler.</span><span class="sxs-lookup"><span data-stu-id="518ef-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="518ef-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="518ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="518ef-105">Parameters</span></span>  
 <span data-ttu-id="518ef-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="518ef-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="518ef-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="518ef-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="518ef-108">geriye doğru izleme başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru izleme tamamlanamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="518ef-108">if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="518ef-109">Döndürülen HRESULT başarısız olan bir Icordebug API'leri döndürür `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="518ef-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="518ef-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="518ef-110">Remarks</span></span>  
 <span data-ttu-id="518ef-111">Yığın değişkeni, ilerleme, bu sonuç kılar emin olmalısınız çağrısı `Next` başarısız döndüreceği HRESULT veya `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="518ef-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="518ef-112">Döndüren `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="518ef-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="518ef-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="518ef-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518ef-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="518ef-114">Requirements</span></span>  
 <span data-ttu-id="518ef-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="518ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="518ef-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="518ef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="518ef-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="518ef-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="518ef-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="518ef-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="518ef-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="518ef-119">See also</span></span>

- [<span data-ttu-id="518ef-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="518ef-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="518ef-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="518ef-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
