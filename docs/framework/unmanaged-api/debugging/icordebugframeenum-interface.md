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
ms.openlocfilehash: 4277a552d217ad7f601bfe72cae32a1f25dd6be4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696238"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="fb721-102">ICorDebugFrameEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb721-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="fb721-103">Icordebugger Genum yöntemlerini uygular ve ICorDebugFrame dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fb721-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb721-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb721-104">Methods</span></span>  
  
|<span data-ttu-id="fb721-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fb721-105">Method</span></span>|<span data-ttu-id="fb721-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb721-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb721-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb721-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="fb721-108">`ICorDebugFrame`Geçerli konumdan başlayarak Numaralandırmadaki belirtilen örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fb721-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb721-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb721-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb721-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fb721-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb721-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb721-111">Requirements</span></span>  

 <span data-ttu-id="fb721-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb721-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb721-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb721-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb721-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fb721-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb721-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb721-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb721-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb721-116">See also</span></span>

- [<span data-ttu-id="fb721-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb721-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
