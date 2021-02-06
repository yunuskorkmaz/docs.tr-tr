---
description: ': ICorDebugThreadEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 088b9bd56ae0049ad5f287b07cd2857f70a496c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658485"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="b3a47-103">ICorDebugThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3a47-103">ICorDebugThreadEnum Interface</span></span>

<span data-ttu-id="b3a47-104">Icordebugger Genum yöntemlerini uygular ve ICorDebugThread dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b3a47-104">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3a47-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b3a47-105">Methods</span></span>  
  
|<span data-ttu-id="b3a47-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b3a47-106">Method</span></span>|<span data-ttu-id="b3a47-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3a47-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3a47-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3a47-108">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="b3a47-109">`ICorDebugThread`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b3a47-109">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3a47-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3a47-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3a47-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b3a47-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a47-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3a47-112">Requirements</span></span>  

 <span data-ttu-id="b3a47-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a47-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a47-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3a47-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3a47-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b3a47-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a47-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a47-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a47-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3a47-117">See also</span></span>

- [<span data-ttu-id="b3a47-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b3a47-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
