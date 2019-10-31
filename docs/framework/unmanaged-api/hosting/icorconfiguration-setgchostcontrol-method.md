---
title: ICorConfiguration::SetGCHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 5a32fb0480e76f47495590a29c329f54722e2dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127777"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="ce5d7-102">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce5d7-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="ce5d7-103">Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce5d7-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce5d7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce5d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce5d7-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="ce5d7-106">'ndaki Atık toplayıcısının, sanal bellek sınırlarını değiştirmesini sağlamak üzere konak istemesine izin veren bir [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ce5d7-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce5d7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce5d7-107">Requirements</span></span>  
 <span data-ttu-id="ce5d7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce5d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce5d7-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce5d7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce5d7-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ce5d7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce5d7-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce5d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5d7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5d7-112">See also</span></span>

- [<span data-ttu-id="ce5d7-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce5d7-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
