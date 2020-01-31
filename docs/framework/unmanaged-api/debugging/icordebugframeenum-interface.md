---
title: ICorDebugFrameEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 6cc1ef5f778902efaa53156fbefe334046c82114
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794532"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="39491-102">ICorDebugFrameEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39491-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="39491-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugFrame dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="39491-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39491-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="39491-104">Methods</span></span>  
  
|<span data-ttu-id="39491-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39491-105">Method</span></span>|<span data-ttu-id="39491-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39491-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39491-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39491-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="39491-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen `ICorDebugFrame` örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="39491-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39491-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39491-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39491-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="39491-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39491-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39491-111">Requirements</span></span>  
 <span data-ttu-id="39491-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39491-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39491-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39491-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39491-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39491-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39491-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39491-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39491-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39491-116">See also</span></span>

- [<span data-ttu-id="39491-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="39491-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
