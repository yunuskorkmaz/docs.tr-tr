---
title: ICorDebugThreadEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: ca7668f23671721477c561774bab03279c4c18c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678564"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="77fd8-102">ICorDebugThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77fd8-102">ICorDebugThreadEnum Interface</span></span>

<span data-ttu-id="77fd8-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugThread dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="77fd8-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77fd8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="77fd8-104">Methods</span></span>  
  
|<span data-ttu-id="77fd8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77fd8-105">Method</span></span>|<span data-ttu-id="77fd8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77fd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77fd8-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77fd8-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="77fd8-108">`ICorDebugThread`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="77fd8-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77fd8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77fd8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77fd8-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="77fd8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77fd8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77fd8-111">Requirements</span></span>  

 <span data-ttu-id="77fd8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fd8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fd8-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="77fd8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77fd8-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="77fd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77fd8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fd8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77fd8-116">See also</span></span>

- [<span data-ttu-id="77fd8-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="77fd8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
