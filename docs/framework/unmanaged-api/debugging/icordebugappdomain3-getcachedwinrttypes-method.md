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
ms.openlocfilehash: 73a08e83d67c973294938a030b95b906aec6be6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126613"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="dcb7a-102">ICorDebugAppDomain3::GetCachedWinRTTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="dcb7a-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="dcb7a-103">Önbelleğe alınmış tüm için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri.</span><span class="sxs-lookup"><span data-stu-id="dcb7a-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcb7a-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcb7a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcb7a-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="dcb7a-106">[out] Bir işaretçi bir [Icordebugguidtotypeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) yönetilen temsillerini numaralandırabilirsiniz arabirimi nesnesi [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri uygulama etki alanında şu anda yüklü.</span><span class="sxs-lookup"><span data-stu-id="dcb7a-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb7a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcb7a-107">Requirements</span></span>  
 **<span data-ttu-id="dcb7a-108">Platformlar:</span><span class="sxs-lookup"><span data-stu-id="dcb7a-108">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="dcb7a-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcb7a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcb7a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcb7a-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="dcb7a-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="dcb7a-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dcb7a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcb7a-112">See also</span></span>

- [<span data-ttu-id="dcb7a-113">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcb7a-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
