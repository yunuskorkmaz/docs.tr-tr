---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6392d1040c9d76944f79dc3a39213ae6c2191bef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415574"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="c4488-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4488-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="c4488-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modüller hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c4488-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="c4488-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c4488-104">Method</span></span>  
  
|<span data-ttu-id="c4488-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c4488-105">Method</span></span>|<span data-ttu-id="c4488-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4488-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4488-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4488-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="c4488-108">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="c4488-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4488-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4488-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4488-110">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4488-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c4488-111">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="c4488-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4488-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4488-112">Requirements</span></span>  
 <span data-ttu-id="c4488-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4488-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4488-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4488-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4488-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4488-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4488-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4488-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4488-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4488-117">See Also</span></span>  
 [<span data-ttu-id="c4488-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c4488-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c4488-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c4488-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
