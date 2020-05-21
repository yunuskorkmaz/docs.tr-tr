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
ms.openlocfilehash: e648b36a2b276d9335eefaf71b57ad76f9fe0def
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762389"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="487c3-102">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="487c3-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="487c3-103">Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="487c3-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487c3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="487c3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="487c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="487c3-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="487c3-106">'ndaki Atık toplayıcısının, sanal bellek sınırlarını değiştirmesini sağlamak üzere konak istemesine izin veren bir [IGCHostControl](igchostcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="487c3-106">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="487c3-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="487c3-107">Requirements</span></span>  
 <span data-ttu-id="487c3-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="487c3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487c3-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="487c3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="487c3-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="487c3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="487c3-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487c3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487c3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="487c3-112">See also</span></span>

- [<span data-ttu-id="487c3-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="487c3-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
