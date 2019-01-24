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
ms.openlocfilehash: 7d471ac13061cfb3a0320801445fb5c931718691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562936"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="db324-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db324-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="db324-103">Yönetilen hata ayıklayıcı bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="db324-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db324-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db324-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db324-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db324-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="db324-106">[out] Bir değer için bir işaretçi `true` yönetilen hata ayıklayıcı işleme bağlı; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="db324-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db324-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db324-107">Requirements</span></span>  
 <span data-ttu-id="db324-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db324-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db324-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db324-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db324-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="db324-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db324-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db324-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db324-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db324-112">See also</span></span>
- [<span data-ttu-id="db324-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db324-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
