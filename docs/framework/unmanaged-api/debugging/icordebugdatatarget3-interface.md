---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965210"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="39d55-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39d55-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="39d55-103">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="39d55-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="39d55-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39d55-104">Method</span></span>  
  
|<span data-ttu-id="39d55-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39d55-105">Method</span></span>|<span data-ttu-id="39d55-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39d55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39d55-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39d55-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="39d55-108">Şu ana kadar yüklü modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="39d55-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39d55-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39d55-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39d55-110">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39d55-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="39d55-111">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="39d55-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d55-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39d55-112">Requirements</span></span>  
 <span data-ttu-id="39d55-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d55-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d55-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39d55-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39d55-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39d55-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39d55-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d55-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d55-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39d55-117">See also</span></span>

- [<span data-ttu-id="39d55-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="39d55-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="39d55-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="39d55-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
