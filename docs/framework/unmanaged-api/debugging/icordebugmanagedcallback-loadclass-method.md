---
title: ICorDebugManagedCallback::LoadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: d23b695550c8444264934f7aca4fa185064e89c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130734"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="75fb0-102">ICorDebugManagedCallback::LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75fb0-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="75fb0-103">Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="75fb0-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75fb0-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75fb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75fb0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="75fb0-106">'ndaki Sınıfın yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75fb0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="75fb0-107">'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75fb0-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75fb0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75fb0-108">Remarks</span></span>  
 <span data-ttu-id="75fb0-109">Bu geri çağırma, yalnızca sınıf yüklemesi sınıfı içeren modül için etkinleştirildiyse oluşur.</span><span class="sxs-lookup"><span data-stu-id="75fb0-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="75fb0-110">Sınıf yükleme her zaman dinamik modüller için etkindir.</span><span class="sxs-lookup"><span data-stu-id="75fb0-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="75fb0-111">`LoadClass` geri çağırması, kesme noktalarını dinamik modüllerde yeni oluşturulan sınıflara bağlamak için uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="75fb0-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75fb0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75fb0-112">Requirements</span></span>  
 <span data-ttu-id="75fb0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75fb0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75fb0-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75fb0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75fb0-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75fb0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75fb0-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75fb0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75fb0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75fb0-117">See also</span></span>

- [<span data-ttu-id="75fb0-118">UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75fb0-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="75fb0-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75fb0-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
