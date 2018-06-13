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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5492d4e1245c6c0ce5c1eb98d25168c5d69d123b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423708"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="e7ffe-102">ICorPublishProcess::EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7ffe-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="e7ffe-103">Bu tarafından başvurulan işleminde uygulama etki alanları için bir numaralandırıcı alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e7ffe-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ffe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7ffe-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7ffe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7ffe-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e7ffe-106">[out] Adresine bir işaretçi bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) uygulama etki alanları bu süreçte koleksiyonu üzerinden yineleme verir örneği.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7ffe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7ffe-107">Remarks</span></span>  
 <span data-ttu-id="e7ffe-108">Mevcut uygulama etki alanları üzerinde bir anlık görüntü temelinde uygulama etki alanları listesi olduğunda `EnumAppDomains` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="e7ffe-109">Bu yöntem, yeni güncel listesini oluşturmak için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="e7ffe-110">Varolan listeleri bu yöntem sonraki çağrılar tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="e7ffe-111">İşlem sonlandırıldı, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değerle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ffe-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7ffe-112">Requirements</span></span>  
 <span data-ttu-id="e7ffe-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7ffe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ffe-114">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e7ffe-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e7ffe-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ffe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ffe-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ffe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ffe-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ffe-117">See Also</span></span>  
 [<span data-ttu-id="e7ffe-118">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7ffe-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
