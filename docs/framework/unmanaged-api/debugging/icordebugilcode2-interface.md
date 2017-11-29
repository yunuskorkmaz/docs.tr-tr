---
title: ICorDebugILCode2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fd6b7b6b097010a307abbc260cda7c4b73e0f00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="57caf-102">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57caf-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="57caf-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="57caf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="57caf-104">Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) bir işlevin yerel değişken imza için belirteci dönün ve Profil Oluşturucu'nın Araçlı Ara dile (IL) eşleme yöntemlerini sağlamak üzere arabirimi kaydırır IL özgün yöntemi kaydırır.</span><span class="sxs-lookup"><span data-stu-id="57caf-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57caf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57caf-105">Methods</span></span>  
  
|<span data-ttu-id="57caf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="57caf-106">Method</span></span>|<span data-ttu-id="57caf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57caf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57caf-108">Getınstrumentedılmap yöntemi</span><span class="sxs-lookup"><span data-stu-id="57caf-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="57caf-109">Bu örnek için özgün yöntemi IL uzaklık için IL uzaklıkları profil oluşturucu eşlemesinden izlenmiş döndürür.</span><span class="sxs-lookup"><span data-stu-id="57caf-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="57caf-110">GetLocalVarSigToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="57caf-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="57caf-111">Meta veriler bu örneği tarafından temsil edilen işlevi için yerel değişken İmza belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="57caf-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57caf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57caf-112">Requirements</span></span>  
 <span data-ttu-id="57caf-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57caf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57caf-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57caf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57caf-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57caf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57caf-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57caf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57caf-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57caf-117">See Also</span></span>  
 [<span data-ttu-id="57caf-118">Icordebugılcode arabirimi</span><span class="sxs-lookup"><span data-stu-id="57caf-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="57caf-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57caf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="57caf-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="57caf-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
