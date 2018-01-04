---
title: "Icordebugılframe2 Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2
helpviewer_keywords: ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef3cc011afebc98e57bffbf0cba2a90cd28e3a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="d4a02-102">Icordebugılframe2 Interface1</span><span class="sxs-lookup"><span data-stu-id="d4a02-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="d4a02-103">Icordebugılframe arabirimi mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d4a02-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4a02-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4a02-104">Methods</span></span>  
  
|<span data-ttu-id="d4a02-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4a02-105">Method</span></span>|<span data-ttu-id="d4a02-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4a02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4a02-107">EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4a02-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="d4a02-108">İçeren bir Icordebugtypeenum nesne alır <xref:System.Type> bu çerçevesinde parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d4a02-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="d4a02-109">RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4a02-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="d4a02-110">Düzenlenen işlevi yeni MSIL uzaklık belirterek remaps.</span><span class="sxs-lookup"><span data-stu-id="d4a02-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4a02-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4a02-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4a02-112">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4a02-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4a02-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4a02-113">Requirements</span></span>  
 <span data-ttu-id="d4a02-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4a02-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4a02-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4a02-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4a02-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4a02-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4a02-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4a02-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a02-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4a02-118">See Also</span></span>  
 [<span data-ttu-id="d4a02-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4a02-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
