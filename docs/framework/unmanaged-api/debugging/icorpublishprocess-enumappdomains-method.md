---
description: ': ICorPublishProcess:: Trmappdomains yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c7834b23967ab467c1589ee31929bf346b4b3b8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794617"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="97382-103">ICorPublishProcess::EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97382-103">ICorPublishProcess::EnumAppDomains Method</span></span>

<span data-ttu-id="97382-104">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="97382-104">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97382-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97382-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97382-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97382-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="97382-107">dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97382-107">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97382-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97382-108">Remarks</span></span>  

 <span data-ttu-id="97382-109">Uygulama etki alanlarının listesi, yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır `EnumAppDomains` .</span><span class="sxs-lookup"><span data-stu-id="97382-109">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="97382-110">Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="97382-110">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="97382-111">Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="97382-111">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="97382-112">İşlem sonlandırıldıysa, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değeriyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="97382-112">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97382-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97382-113">Requirements</span></span>  

 <span data-ttu-id="97382-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97382-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97382-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="97382-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="97382-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97382-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97382-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97382-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97382-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97382-118">See also</span></span>

- [<span data-ttu-id="97382-119">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97382-119">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
