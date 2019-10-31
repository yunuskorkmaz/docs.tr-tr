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
ms.openlocfilehash: 7f0570b668cc33ca509c8522d1ba35ebcfca2453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125581"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="ad79c-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad79c-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="ad79c-103">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad79c-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad79c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad79c-104">Methods</span></span>  
  
|<span data-ttu-id="ad79c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad79c-105">Method</span></span>|<span data-ttu-id="ad79c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad79c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad79c-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad79c-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="ad79c-108">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="ad79c-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="ad79c-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad79c-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="ad79c-110">Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="ad79c-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad79c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad79c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad79c-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ad79c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad79c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad79c-113">Requirements</span></span>  
 <span data-ttu-id="ad79c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad79c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad79c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad79c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad79c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad79c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad79c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad79c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad79c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad79c-118">See also</span></span>

- [<span data-ttu-id="ad79c-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad79c-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="ad79c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad79c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
