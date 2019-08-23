---
title: ICorDebugModuleEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682fe190126d4f40013678d996804e9f3481bc02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965077"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="0301a-102">ICorDebugModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0301a-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="0301a-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugModule dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0301a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0301a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0301a-104">Methods</span></span>  
  
|<span data-ttu-id="0301a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0301a-105">Method</span></span>|<span data-ttu-id="0301a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0301a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0301a-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0301a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="0301a-108">Geçerli konumdan başlayarak Numaralandırmadaki `ICorDebugModule` belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0301a-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0301a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0301a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0301a-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="0301a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0301a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0301a-111">Requirements</span></span>  
 <span data-ttu-id="0301a-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0301a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0301a-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0301a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0301a-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0301a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0301a-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0301a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0301a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0301a-116">See also</span></span>

- [<span data-ttu-id="0301a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0301a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
