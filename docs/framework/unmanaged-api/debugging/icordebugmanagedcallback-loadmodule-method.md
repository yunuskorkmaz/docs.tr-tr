---
description: ': ICorDebugManagedCallback:: LoadModule yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9a547d384b3f450054ebc70072664c6dcfb5992f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660512"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="7c2c3-103">ICorDebugManagedCallback::LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c2c3-103">ICorDebugManagedCallback::LoadModule Method</span></span>

<span data-ttu-id="7c2c3-104">Bir ortak dil çalışma zamanı (CLR) modülünün başarıyla yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="7c2c3-104">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c2c3-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c2c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c2c3-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="7c2c3-107">'ndaki Modülün yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c2c3-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="7c2c3-108">'ndaki CLR modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c2c3-108">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c2c3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c2c3-109">Remarks</span></span>  

 <span data-ttu-id="7c2c3-110">`LoadModule`Geri çağırma, modülün meta verilerini incelemek, Just-In-Time (JIT) derleyici bayraklarını ayarlamak ya da modül için sınıf yükleme geri çağırmaları etkinleştirmek veya devre dışı bırakmak için uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c2c3-110">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c2c3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c2c3-111">Requirements</span></span>  

 <span data-ttu-id="7c2c3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2c3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2c3-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c2c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c2c3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7c2c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c2c3-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2c3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2c3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c2c3-116">See also</span></span>

- [<span data-ttu-id="7c2c3-117">UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c2c3-117">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="7c2c3-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c2c3-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
