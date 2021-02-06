---
description: ': ICorDebugManagedCallback:: UnloadClass Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::UnloadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: b76caf39611b0f59c74b4ae47d167e6f232a6dbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660225"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="d8149-103">ICorDebugManagedCallback::UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8149-103">ICorDebugManagedCallback::UnloadClass Method</span></span>

<span data-ttu-id="d8149-104">Hata ayıklayıcıya bir sınıfın bellekten kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8149-104">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8149-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8149-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8149-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8149-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d8149-107">'ndaki Sınıfını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8149-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="d8149-108">'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8149-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8149-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8149-109">Remarks</span></span>  

 <span data-ttu-id="d8149-110">Bu çağrıdan sonra sınıfa başvurulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8149-110">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8149-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8149-111">Requirements</span></span>  

 <span data-ttu-id="d8149-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8149-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8149-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8149-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8149-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8149-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8149-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8149-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8149-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8149-116">See also</span></span>

- [<span data-ttu-id="d8149-117">LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8149-117">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="d8149-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8149-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
