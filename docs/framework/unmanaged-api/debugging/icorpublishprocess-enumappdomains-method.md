---
title: ICorPublishProcess::EnumAppDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: aa76bf511ff1e1710a7ff86ad2ac97665969f2bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140441"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="c737e-102">ICorPublishProcess::EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c737e-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="c737e-103">Bu [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="c737e-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c737e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c737e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c737e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c737e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c737e-106">dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c737e-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c737e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c737e-107">Remarks</span></span>  
 <span data-ttu-id="c737e-108">Uygulama etki alanlarının listesi, `EnumAppDomains` yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="c737e-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="c737e-109">Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c737e-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="c737e-110">Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="c737e-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="c737e-111">İşlem sonlandırılırsa, `EnumAppDomains` HRESULT değeri CORDBG_E_PROCESS_TERMINATED ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c737e-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c737e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c737e-112">Requirements</span></span>  
 <span data-ttu-id="c737e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c737e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c737e-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c737e-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c737e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c737e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c737e-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c737e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c737e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c737e-117">See also</span></span>

- [<span data-ttu-id="c737e-118">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c737e-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
