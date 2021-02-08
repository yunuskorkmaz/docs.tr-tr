---
description: ': ICorDebugAppDomain3:: GetCachedWinRTTypes metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 813fb6c05d5e1e5f119424c6e983b86b3ff5889d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772243"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="c88c9-103">ICorDebugAppDomain3::GetCachedWinRTTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="c88c9-103">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>

<span data-ttu-id="c88c9-104">Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="c88c9-104">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c88c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c88c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c88c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c88c9-106">Parameters</span></span>  

 `ppGuidToTypeEnum`  
 <span data-ttu-id="c88c9-107">dışı Bir [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) arabirim nesnesine yönelik bir işaretçi, uygulama etki alanında şu anda yüklü olan Windows çalışma zamanı türlerinin yönetilen gösterimlerini numaralandırabilirler.</span><span class="sxs-lookup"><span data-stu-id="c88c9-107">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c88c9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c88c9-108">Requirements</span></span>  

 <span data-ttu-id="c88c9-109">**Platformlar:** Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="c88c9-109">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c88c9-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c88c9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c88c9-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c88c9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c88c9-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c88c9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88c9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c88c9-113">See also</span></span>

- [<span data-ttu-id="c88c9-114">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c88c9-114">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
