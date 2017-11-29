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
ms.openlocfilehash: baa8ea056c457455482a5f7631956f7edce0ac91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="aa7dd-102">Icordebugobjectenum Interface1</span><span class="sxs-lookup"><span data-stu-id="aa7dd-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="aa7dd-103">Icordebugenum yöntemlerini uygular ve bunların göreli sanal adresler (RVAs) tarafından nesne dizileri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa7dd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa7dd-104">Methods</span></span>  
  
|<span data-ttu-id="aa7dd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aa7dd-105">Method</span></span>|<span data-ttu-id="aa7dd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa7dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa7dd-107">Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa7dd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="aa7dd-108">Belirtilen nesne sayısını RVAs geçerli konumdan başlayarak numaralandırması alır.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa7dd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa7dd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa7dd-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa7dd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa7dd-111">Requirements</span></span>  
 <span data-ttu-id="aa7dd-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa7dd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa7dd-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa7dd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa7dd-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa7dd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa7dd-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa7dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7dd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa7dd-116">See Also</span></span>  
 [<span data-ttu-id="aa7dd-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aa7dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
