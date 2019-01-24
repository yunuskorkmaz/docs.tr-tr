---
title: ICorDebugAppDomain3::GetCachedWinRTTypes Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afbe368d58c96c8ddc97ccc3bb077ce768b229b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566118"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="4a0db-102">ICorDebugAppDomain3::GetCachedWinRTTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="4a0db-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="4a0db-103">Önbelleğe alınmış tüm için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri.</span><span class="sxs-lookup"><span data-stu-id="4a0db-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a0db-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a0db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a0db-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="4a0db-106">[out] Bir işaretçi bir [Icordebugguidtotypeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) yönetilen temsillerini numaralandırabilirsiniz arabirimi nesnesi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri uygulama etki alanında şu anda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4a0db-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0db-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a0db-107">Requirements</span></span>  
 <span data-ttu-id="4a0db-108">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0db-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="4a0db-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a0db-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a0db-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a0db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a0db-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a0db-112">See also</span></span>
- [<span data-ttu-id="4a0db-113">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a0db-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
