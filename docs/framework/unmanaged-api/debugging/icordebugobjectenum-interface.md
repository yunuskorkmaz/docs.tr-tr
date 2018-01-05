---
title: Icordebugobjectenum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum
helpviewer_keywords: ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f2610600d102177c80821c78e7d07f8aed1b6de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="d8ad4-102">Icordebugobjectenum Interface1</span><span class="sxs-lookup"><span data-stu-id="d8ad4-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="d8ad4-103">Icordebugenum yöntemlerini uygular ve bunların göreli sanal adresler (RVAs) tarafından nesne dizileri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d8ad4-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8ad4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d8ad4-104">Methods</span></span>  
  
|<span data-ttu-id="d8ad4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d8ad4-105">Method</span></span>|<span data-ttu-id="d8ad4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ad4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8ad4-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ad4-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="d8ad4-108">Belirtilen nesne sayısını RVAs geçerli konumdan başlayarak numaralandırması alır.</span><span class="sxs-lookup"><span data-stu-id="d8ad4-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ad4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ad4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8ad4-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d8ad4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ad4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ad4-111">Requirements</span></span>  
 <span data-ttu-id="d8ad4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ad4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ad4-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ad4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ad4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ad4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ad4-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ad4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ad4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ad4-116">See Also</span></span>  
 [<span data-ttu-id="d8ad4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8ad4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
