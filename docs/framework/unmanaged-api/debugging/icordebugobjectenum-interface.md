---
title: ICorDebugObjectEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157786"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="5811d-102">ICorDebugObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5811d-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="5811d-103">Icordebugenum yöntemlerini uygular ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5811d-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5811d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5811d-104">Methods</span></span>  
  
|<span data-ttu-id="5811d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5811d-105">Method</span></span>|<span data-ttu-id="5811d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5811d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5811d-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5811d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="5811d-108">RVA belirli sayıda nesneleri, geçerli konumdan başlayarak sabit listesi alır.</span><span class="sxs-lookup"><span data-stu-id="5811d-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5811d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5811d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5811d-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5811d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5811d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5811d-111">Requirements</span></span>  
 <span data-ttu-id="5811d-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5811d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5811d-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5811d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5811d-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5811d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5811d-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5811d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5811d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5811d-116">See also</span></span>

- [<span data-ttu-id="5811d-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5811d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
