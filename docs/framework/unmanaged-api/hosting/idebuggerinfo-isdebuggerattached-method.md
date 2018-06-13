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
ms.openlocfilehash: 91acfa5545f3115c9e95207f05708ff32530994f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437287"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="ce438-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce438-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="ce438-103">Bu işlem için yönetilen bir hata ayıklayıcısı ekli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ce438-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce438-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce438-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce438-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce438-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="ce438-106">[out] Bir değer için bir işaretçi `true` yönetilen bir hata ayıklayıcısı ekli işlemine; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="ce438-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce438-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce438-107">Requirements</span></span>  
 <span data-ttu-id="ce438-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce438-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce438-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce438-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce438-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ce438-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce438-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce438-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce438-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce438-112">See Also</span></span>  
 [<span data-ttu-id="ce438-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce438-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
