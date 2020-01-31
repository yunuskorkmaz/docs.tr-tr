---
title: ICorDebugManagedCallback::LoadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777134"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="364cf-102">ICorDebugManagedCallback::LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="364cf-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="364cf-103">Bir ortak dil çalışma zamanı (CLR) modülünün başarıyla yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="364cf-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="364cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="364cf-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="364cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="364cf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="364cf-106">'ndaki Modülün yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="364cf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="364cf-107">'ndaki CLR modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="364cf-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="364cf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="364cf-108">Remarks</span></span>  
 <span data-ttu-id="364cf-109">`LoadModule` geri çağırması, modülün meta verilerini incelemek, Just-In-Time (JıT) derleyici bayraklarını ayarlamak ya da modül için sınıf yükleme geri çağırmaları etkinleştirmek veya devre dışı bırakmak için uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="364cf-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="364cf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="364cf-110">Requirements</span></span>  
 <span data-ttu-id="364cf-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="364cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="364cf-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="364cf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="364cf-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="364cf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="364cf-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="364cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="364cf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="364cf-115">See also</span></span>

- [<span data-ttu-id="364cf-116">UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="364cf-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="364cf-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="364cf-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
