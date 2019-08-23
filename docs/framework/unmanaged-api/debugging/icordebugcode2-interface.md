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
ms.openlocfilehash: 9cb7be64089a55e7b653fcd6272219abba311af8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960804"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="6ec44-102">ICorDebugCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ec44-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="6ec44-103">"ICorDebugCode" yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ec44-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ec44-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ec44-104">Methods</span></span>  
  
|<span data-ttu-id="6ec44-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6ec44-105">Method</span></span>|<span data-ttu-id="6ec44-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ec44-107">GetCodeChunks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ec44-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="6ec44-108">Bu kod nesnesinin oluştuğu kod öbeklerini alır.</span><span class="sxs-lookup"><span data-stu-id="6ec44-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="6ec44-109">GetCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ec44-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="6ec44-110">Bu kod nesnesinin yerel görüntü Oluşturucu (Ngen. exe) kullanılarak derlenen veya oluşturulan koşulları belirten bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="6ec44-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ec44-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ec44-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ec44-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6ec44-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec44-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ec44-113">Requirements</span></span>  
 <span data-ttu-id="6ec44-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec44-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec44-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ec44-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ec44-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6ec44-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ec44-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec44-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec44-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ec44-118">See also</span></span>

- [<span data-ttu-id="6ec44-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ec44-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="6ec44-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ec44-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
