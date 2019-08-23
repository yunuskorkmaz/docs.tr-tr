---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee94e25201dee4999fd5acb2be44a80454e9efbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911409"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="feaa7-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feaa7-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="feaa7-103">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="feaa7-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="feaa7-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="feaa7-104">Method</span></span>  
  
|<span data-ttu-id="feaa7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="feaa7-105">Method</span></span>|<span data-ttu-id="feaa7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feaa7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="feaa7-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feaa7-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="feaa7-108">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="feaa7-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feaa7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feaa7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feaa7-110">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="feaa7-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="feaa7-111">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="feaa7-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feaa7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feaa7-112">Requirements</span></span>  
 <span data-ttu-id="feaa7-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feaa7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feaa7-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="feaa7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="feaa7-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="feaa7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feaa7-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feaa7-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feaa7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feaa7-117">See also</span></span>

- [<span data-ttu-id="feaa7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="feaa7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="feaa7-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="feaa7-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
