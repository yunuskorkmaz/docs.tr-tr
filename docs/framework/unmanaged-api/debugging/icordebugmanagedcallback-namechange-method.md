---
title: ICorDebugManagedCallback::NameChange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212678"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="1dbde-102">ICorDebugManagedCallback::NameChange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dbde-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="1dbde-103">Hata ayıklayıcıya bir uygulama etki alanı ya da bir iş parçacığının adının değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1dbde-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dbde-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dbde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dbde-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1dbde-106">'ndaki Bir ad değişikliğine sahip olan ya da bir ad değişikliğine sahip iş parçacığını içeren bir ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dbde-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1dbde-107">'ndaki Bir ad değişikliği olan iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dbde-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dbde-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dbde-108">Requirements</span></span>  
 <span data-ttu-id="1dbde-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dbde-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dbde-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1dbde-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dbde-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1dbde-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dbde-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dbde-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbde-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dbde-113">See also</span></span>

- [<span data-ttu-id="1dbde-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dbde-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
