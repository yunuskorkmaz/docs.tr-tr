---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 04e7b9a064d4a06a06b8a1518f06092ba79a3561
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783487"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="7a2c2-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a2c2-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="7a2c2-103">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="7a2c2-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="7a2c2-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a2c2-104">Method</span></span>  
  
|<span data-ttu-id="7a2c2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a2c2-105">Method</span></span>|<span data-ttu-id="7a2c2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a2c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a2c2-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a2c2-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="7a2c2-108">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="7a2c2-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a2c2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a2c2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a2c2-110">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a2c2-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7a2c2-111">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="7a2c2-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a2c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a2c2-112">Requirements</span></span>  
 <span data-ttu-id="7a2c2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a2c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a2c2-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a2c2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a2c2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a2c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a2c2-116">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a2c2-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2c2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a2c2-117">See also</span></span>

- [<span data-ttu-id="7a2c2-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a2c2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7a2c2-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a2c2-119">Debugging</span></span>](index.md)
