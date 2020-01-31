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
ms.openlocfilehash: 6de2cb7c1a1423c5bd38a6f2e5d01c39166ab119
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791327"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="ba669-102">ICorDebugThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba669-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="ba669-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugThread dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ba669-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba669-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ba669-104">Methods</span></span>  
  
|<span data-ttu-id="ba669-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ba669-105">Method</span></span>|<span data-ttu-id="ba669-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba669-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba669-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba669-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="ba669-108">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen `ICorDebugThread` örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ba669-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba669-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba669-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba669-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ba669-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba669-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba669-111">Requirements</span></span>  
 <span data-ttu-id="ba669-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba669-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba669-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba669-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba669-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba669-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba669-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba669-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba669-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba669-116">See also</span></span>

- [<span data-ttu-id="ba669-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba669-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
