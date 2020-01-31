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
ms.openlocfilehash: b019c198635373fa6aaea01914dc9747b7486ae0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792887"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="365d1-102">ICorDebugModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="365d1-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="365d1-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugModule dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="365d1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="365d1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="365d1-104">Methods</span></span>  
  
|<span data-ttu-id="365d1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="365d1-105">Method</span></span>|<span data-ttu-id="365d1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="365d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="365d1-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="365d1-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="365d1-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen `ICorDebugModule` örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="365d1-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="365d1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="365d1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="365d1-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="365d1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="365d1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="365d1-111">Requirements</span></span>  
 <span data-ttu-id="365d1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="365d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="365d1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="365d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="365d1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="365d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="365d1-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365d1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="365d1-116">See also</span></span>

- [<span data-ttu-id="365d1-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="365d1-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
