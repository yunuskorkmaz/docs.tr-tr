---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f97a6819c413c79eb8431c9a101249d459b0155
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545257"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="df291-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df291-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="df291-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="df291-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="df291-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df291-104">Method</span></span>  
  
|<span data-ttu-id="df291-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="df291-105">Method</span></span>|<span data-ttu-id="df291-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df291-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df291-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df291-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="df291-108">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="df291-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df291-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df291-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df291-110">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df291-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="df291-111">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="df291-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df291-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df291-112">Requirements</span></span>  
 <span data-ttu-id="df291-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df291-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df291-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df291-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df291-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df291-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df291-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df291-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df291-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df291-117">See also</span></span>
- [<span data-ttu-id="df291-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df291-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="df291-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="df291-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
