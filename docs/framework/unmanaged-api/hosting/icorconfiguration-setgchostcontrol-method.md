---
description: ': ICorConfiguration:: SetGCHostControl Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4d3d6e5e5275adf02f9d693234a5c8e77714fd03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636656"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="f129e-103">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f129e-103">ICorConfiguration::SetGCHostControl Method</span></span>

<span data-ttu-id="f129e-104">Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f129e-104">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f129e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f129e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f129e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f129e-106">Parameters</span></span>  

 `pGCHostControl`  
 <span data-ttu-id="f129e-107">'ndaki Atık toplayıcısının, sanal bellek sınırlarını değiştirmesini sağlamak üzere konak istemesine izin veren bir [IGCHostControl](igchostcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f129e-107">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f129e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f129e-108">Requirements</span></span>  

 <span data-ttu-id="f129e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f129e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f129e-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f129e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f129e-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f129e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f129e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f129e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f129e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f129e-113">See also</span></span>

- [<span data-ttu-id="f129e-114">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f129e-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
