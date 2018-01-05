---
title: "ICorDebugManagedCallback::LoadClass Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e732b418398e9c917085d22507c9304981b06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="158ae-102">ICorDebugManagedCallback::LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158ae-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="158ae-103">Hata ayıklayıcı bir sınıf yüklü olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="158ae-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="158ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="158ae-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="158ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="158ae-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="158ae-106">[in] Bir işaretçi Icordebugappdomain nesneye sınıfı yüklenmiş olan uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158ae-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="158ae-107">[in] Bir işaretçi Icordebugclass nesneye sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="158ae-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="158ae-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="158ae-108">Remarks</span></span>  
 <span data-ttu-id="158ae-109">Yalnızca sınıfı yükleme sınıfı içeren modülü için etkinleştirilmişse bu geri çağırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="158ae-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="158ae-110">Sınıf yükleme dinamik modülleri için her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="158ae-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="158ae-111">`LoadClass` Geri çağırma dinamik modüllerdeki yeni oluşturulan sınıflar kesme noktaları bağlamak için uygun bir saat sağlar.</span><span class="sxs-lookup"><span data-stu-id="158ae-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="158ae-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="158ae-112">Requirements</span></span>  
 <span data-ttu-id="158ae-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="158ae-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="158ae-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="158ae-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="158ae-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="158ae-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="158ae-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="158ae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158ae-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="158ae-117">See Also</span></span>  
 [<span data-ttu-id="158ae-118">UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="158ae-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="158ae-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="158ae-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
