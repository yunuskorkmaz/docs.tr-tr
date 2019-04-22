---
title: ICorDebugILCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a27dbd8b5013937bb97f37113687405c988c1fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142668"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="c213d-102">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c213d-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="c213d-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c213d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c213d-104">Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) yönelik bir işlevin yerel değişken imzası belirtecini döndürür ve bir profil oluşturucunun Araçlı Ara dil (IL) map yöntemleri sağlamak için arabirimi kaydırır IL özgün yöntemi kaydırır.</span><span class="sxs-lookup"><span data-stu-id="c213d-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c213d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c213d-105">Methods</span></span>  
  
|<span data-ttu-id="c213d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c213d-106">Method</span></span>|<span data-ttu-id="c213d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c213d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c213d-108">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c213d-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="c213d-109">Bu örnek için özgün yöntemi IL uzaklık için IL uzaklık bir eşlemden profil oluşturucu izleme eklenmiş döndürür.</span><span class="sxs-lookup"><span data-stu-id="c213d-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="c213d-110">GetLocalVarSigToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c213d-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="c213d-111">Meta veriler için bu örneği tarafından temsil edilen işlev için yerel değişken imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c213d-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c213d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c213d-112">Requirements</span></span>  
 <span data-ttu-id="c213d-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c213d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c213d-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c213d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c213d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c213d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c213d-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c213d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c213d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c213d-117">See also</span></span>

- [<span data-ttu-id="c213d-118">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c213d-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="c213d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c213d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c213d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c213d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
