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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39ce3e8329c4ff32b55341127f68a800246677df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169955"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="46871-102">ICorDebugManagedCallback::LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46871-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="46871-103">Hata ayıklayıcı, bir sınıf yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="46871-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46871-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46871-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46871-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46871-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="46871-106">[in] Sınıf yüklenmiş olan uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="46871-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="46871-107">[in] Bu sınıfın temsil ettiği bir Icordebugclass nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46871-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46871-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46871-108">Remarks</span></span>  
 <span data-ttu-id="46871-109">Sınıf yükleme sınıfı içeren modül için yalnızca etkinleştirildiyse, bu geri çağırma gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="46871-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="46871-110">Sınıf yükleme, dinamik modüller için her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="46871-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="46871-111">`LoadClass` Dinamik modüller yeni oluşturulan sınıflardaki kesme noktaları bağlamak için uygun bir saat geri çağırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="46871-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46871-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46871-112">Requirements</span></span>  
 <span data-ttu-id="46871-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46871-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46871-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46871-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46871-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46871-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46871-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46871-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46871-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46871-117">See also</span></span>

- [<span data-ttu-id="46871-118">UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46871-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="46871-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46871-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
