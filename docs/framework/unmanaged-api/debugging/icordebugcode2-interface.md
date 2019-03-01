---
title: ICorDebugCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964273"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="e0eed-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0eed-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="e0eed-103">"ICorDebugCode" özelliklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0eed-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0eed-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e0eed-104">Methods</span></span>  
  
|<span data-ttu-id="e0eed-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0eed-105">Method</span></span>|<span data-ttu-id="e0eed-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0eed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0eed-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0eed-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="e0eed-108">Bu kod nesnesi oluşan kod öbekleriyle alır.</span><span class="sxs-lookup"><span data-stu-id="e0eed-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="e0eed-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0eed-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="e0eed-110">Koşullar altında bu kod nesnesi ya da tam derleme ya da yerel Görüntü Oluşturucu (Ngen.exe) kullanılarak oluşturulan zamanında (JIT) olduğu belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="e0eed-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0eed-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0eed-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0eed-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e0eed-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0eed-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0eed-113">Requirements</span></span>  
 <span data-ttu-id="e0eed-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0eed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0eed-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0eed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0eed-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0eed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0eed-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0eed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0eed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0eed-118">See also</span></span>

- [<span data-ttu-id="e0eed-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0eed-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="e0eed-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0eed-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
