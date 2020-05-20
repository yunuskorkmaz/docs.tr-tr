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
ms.openlocfilehash: 0c3b5da52b78150198fa9f910bf01b4657e4eba8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421169"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="df94f-102">ICorPublishProcess::EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df94f-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="df94f-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="df94f-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df94f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="df94f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df94f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df94f-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="df94f-106">dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df94f-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df94f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df94f-107">Remarks</span></span>  
 <span data-ttu-id="df94f-108">Uygulama etki alanlarının listesi, yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır `EnumAppDomains` .</span><span class="sxs-lookup"><span data-stu-id="df94f-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="df94f-109">Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="df94f-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="df94f-110">Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="df94f-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="df94f-111">İşlem sonlandırıldıysa, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değeriyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="df94f-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df94f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df94f-112">Requirements</span></span>  
 <span data-ttu-id="df94f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df94f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df94f-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="df94f-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="df94f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df94f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df94f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df94f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df94f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df94f-117">See also</span></span>

- [<span data-ttu-id="df94f-118">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df94f-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
