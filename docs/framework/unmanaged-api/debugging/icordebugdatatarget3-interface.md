---
title: ICorDebugDataTarget3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c65bbfa033a3a585cdcfdb42cdda95f1de4aa412
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="34c2c-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34c2c-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="34c2c-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modüller hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="34c2c-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="34c2c-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="34c2c-104">Method</span></span>  
  
|<span data-ttu-id="34c2c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="34c2c-105">Method</span></span>|<span data-ttu-id="34c2c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34c2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34c2c-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c2c-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="34c2c-108">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="34c2c-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34c2c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c2c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34c2c-110">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34c2c-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="34c2c-111">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="34c2c-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c2c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34c2c-112">Requirements</span></span>  
 <span data-ttu-id="34c2c-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c2c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c2c-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34c2c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34c2c-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34c2c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c2c-116">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c2c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c2c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34c2c-117">See Also</span></span>  
 [<span data-ttu-id="34c2c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34c2c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="34c2c-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="34c2c-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
