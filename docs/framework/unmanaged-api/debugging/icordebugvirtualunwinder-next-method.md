---
title: ICorDebugVirtualUnwinder::Next yöntemi
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076893"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="d757a-102">ICorDebugVirtualUnwinder::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="d757a-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="d757a-103">Arayanın bağlam ilerler.</span><span class="sxs-lookup"><span data-stu-id="d757a-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d757a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d757a-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="d757a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d757a-105">Parameters</span></span>  
 <span data-ttu-id="d757a-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="d757a-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d757a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d757a-107">Return Value</span></span>  
 <span data-ttu-id="d757a-108">`S_OK` geriye doğru izleme başarıyla oluştuysa veya `CORDBG_S_AT_END_OF_STACK` daha fazla çerçeve olmadığından geriye doğru izleme tamamlanamıyorsa.</span><span class="sxs-lookup"><span data-stu-id="d757a-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="d757a-109">Döndürülen HRESULT başarısız olan bir Icordebug API'leri döndürür `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="d757a-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d757a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d757a-110">Remarks</span></span>  
 <span data-ttu-id="d757a-111">Yığın değişkeni, ilerleme, bu sonuç kılar emin olmalısınız çağrısı `Next` başarısız döndüreceği HRESULT veya `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="d757a-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="d757a-112">Döndüren `S_OK` süresiz olarak sonsuz bir döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d757a-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d757a-113">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d757a-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d757a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d757a-114">Requirements</span></span>  
 <span data-ttu-id="d757a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d757a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d757a-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d757a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d757a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d757a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d757a-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d757a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d757a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d757a-119">See also</span></span>

- [<span data-ttu-id="d757a-120">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d757a-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d757a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d757a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
