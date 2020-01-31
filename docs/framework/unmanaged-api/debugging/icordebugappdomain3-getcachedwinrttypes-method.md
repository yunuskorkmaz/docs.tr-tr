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
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784992"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="36ba7-102">ICorDebugAppDomain3::GetCachedWinRTTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="36ba7-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="36ba7-103">Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="36ba7-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ba7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36ba7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="36ba7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36ba7-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="36ba7-106">dışı Bir [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) arabirim nesnesine yönelik bir işaretçi, uygulama etki alanında şu anda yüklü olan Windows çalışma zamanı türlerinin yönetilen gösterimlerini numaralandırabilirler.</span><span class="sxs-lookup"><span data-stu-id="36ba7-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ba7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36ba7-107">Requirements</span></span>  
 <span data-ttu-id="36ba7-108">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="36ba7-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="36ba7-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36ba7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36ba7-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="36ba7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36ba7-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36ba7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ba7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ba7-112">See also</span></span>

- [<span data-ttu-id="36ba7-113">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36ba7-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
