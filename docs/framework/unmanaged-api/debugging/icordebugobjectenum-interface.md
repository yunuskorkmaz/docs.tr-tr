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
ms.openlocfilehash: 1faa78150659b4397cd4174583b607e1f7841b8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943355"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="19273-102">ICorDebugObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19273-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="19273-103">Icorıı Genum yöntemlerini uygular ve nesnelerin dizilerini göreli sanal adresleriyle (RVA) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="19273-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19273-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19273-104">Methods</span></span>  
  
|<span data-ttu-id="19273-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="19273-105">Method</span></span>|<span data-ttu-id="19273-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19273-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19273-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19273-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="19273-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen nesne sayısının RVA alır.</span><span class="sxs-lookup"><span data-stu-id="19273-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19273-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19273-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19273-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="19273-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19273-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19273-111">Requirements</span></span>  
 <span data-ttu-id="19273-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19273-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19273-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19273-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19273-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19273-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19273-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19273-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19273-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19273-116">See also</span></span>

- [<span data-ttu-id="19273-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19273-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
