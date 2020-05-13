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
ms.openlocfilehash: ccb9eff963da1d502d1ed789640f1a108676754c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213354"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="97558-102">ICorDebugModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97558-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="97558-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugModule dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="97558-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97558-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97558-104">Methods</span></span>  
  
|<span data-ttu-id="97558-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97558-105">Method</span></span>|<span data-ttu-id="97558-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97558-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97558-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97558-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="97558-108">`ICorDebugModule`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="97558-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97558-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97558-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97558-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="97558-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97558-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97558-111">Requirements</span></span>  
 <span data-ttu-id="97558-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97558-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97558-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97558-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97558-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="97558-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97558-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97558-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97558-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97558-116">See also</span></span>

- [<span data-ttu-id="97558-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97558-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
