---
description: ': ICorDebugObjectEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d5cd8580bfa81af7d644c2fb11524a43a9062ddf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722249"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="1ba68-103">ICorDebugObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ba68-103">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="1ba68-104">Icorıı Genum yöntemlerini uygular ve nesnelerin dizilerini göreli sanal adresleriyle (RVA) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1ba68-104">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ba68-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1ba68-105">Methods</span></span>  
  
|<span data-ttu-id="1ba68-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1ba68-106">Method</span></span>|<span data-ttu-id="1ba68-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba68-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ba68-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ba68-108">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="1ba68-109">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen nesne sayısının RVA alır.</span><span class="sxs-lookup"><span data-stu-id="1ba68-109">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba68-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ba68-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ba68-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1ba68-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ba68-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ba68-112">Requirements</span></span>  

 <span data-ttu-id="1ba68-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ba68-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ba68-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ba68-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ba68-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ba68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ba68-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba68-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba68-117">See also</span></span>

- [<span data-ttu-id="1ba68-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1ba68-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
