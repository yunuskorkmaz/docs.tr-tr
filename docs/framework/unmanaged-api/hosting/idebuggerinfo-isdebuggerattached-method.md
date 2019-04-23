---
title: IDebuggerInfo::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0708a3b501a99b5f71be5ba4c6cc4ea2b754d12a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191347"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="f970d-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f970d-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="f970d-103">Yönetilen hata ayıklayıcı bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f970d-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f970d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f970d-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f970d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f970d-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="f970d-106">[out] Bir değer için bir işaretçi `true` yönetilen hata ayıklayıcı işleme bağlı; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="f970d-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f970d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f970d-107">Requirements</span></span>  
 <span data-ttu-id="f970d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f970d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f970d-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f970d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f970d-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f970d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f970d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f970d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f970d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f970d-112">See also</span></span>

- [<span data-ttu-id="f970d-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f970d-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
