---
title: ICorDebugCodeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: b611dcabc1e5cc36f5c6342f0a832cc81de8c1d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720743"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="c1a87-102">ICorDebugCodeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a87-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="c1a87-103">"Icordebugger Genum" yöntemlerini uygular ve "ICorDebugCode" dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c1a87-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1a87-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1a87-104">Methods</span></span>  
  
|<span data-ttu-id="c1a87-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c1a87-105">Method</span></span>|<span data-ttu-id="c1a87-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1a87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1a87-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a87-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="c1a87-108">`ICorDebugCode`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c1a87-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a87-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1a87-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1a87-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c1a87-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a87-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a87-111">Requirements</span></span>  

 <span data-ttu-id="c1a87-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a87-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a87-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1a87-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1a87-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c1a87-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1a87-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a87-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a87-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a87-116">See also</span></span>

- [<span data-ttu-id="c1a87-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1a87-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
