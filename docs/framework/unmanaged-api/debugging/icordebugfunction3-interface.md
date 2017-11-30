---
title: ICorDebugFunction3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction3
api_location: mscordbi.dll
api_type: COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfe0c420c1c9b8074b7cb769e592f8cb2f5916e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="eb260-102">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb260-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="eb260-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="eb260-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eb260-104">Mantıksal bir ReJIT isteğinden koduna erişim sağlamak için ICorDebugFunction arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="eb260-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb260-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb260-105">Methods</span></span>  
  
|<span data-ttu-id="eb260-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb260-106">Method</span></span>|<span data-ttu-id="eb260-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb260-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb260-108">Getactiverejitrequestılcode yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb260-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="eb260-109">Bir arabirim işaretçisi alır bir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) etkin bir ReJIT istek IL içerir.</span><span class="sxs-lookup"><span data-stu-id="eb260-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb260-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb260-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb260-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb260-111">Requirements</span></span>  
 <span data-ttu-id="eb260-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb260-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb260-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb260-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb260-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb260-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb260-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb260-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb260-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb260-116">See Also</span></span>  
 [<span data-ttu-id="eb260-117">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb260-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="eb260-118">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eb260-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="eb260-119">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb260-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
