---
title: "ICorDebugProcess5::EnableNGENPolicy Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5::EnableNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd259308494e1a86f0a6cdec8866bb66a1614b76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="86656-102">ICorDebugProcess5::EnableNGENPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86656-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="86656-103">Yönetilen hata ayıklayıcı altında çalışırken yerel görüntüler nasıl bir uygulamanın yüklediği belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86656-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86656-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86656-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86656-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86656-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="86656-106">[in] A [cordebugngenpolicy sabit](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) nasıl yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüler bir uygulamanın yüklediği belirler sabiti.</span><span class="sxs-lookup"><span data-stu-id="86656-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86656-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86656-107">Remarks</span></span>  
 <span data-ttu-id="86656-108">İlke başarılı bir şekilde ayarlanmışsa, yöntem `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="86656-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="86656-109">Varsa `ePolicy` tarafından tanımlanan Enum değerleri aralığı dışında [cordebugngenpolicy sabit](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), yöntem döndürür `E_INVALIDARG` ve yöntem çağrısının etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86656-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="86656-110">Yerel Görüntü Oluşturucu (Ngen.exe) ilkesi güncelleştirilemiyor ise, yöntem `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="86656-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="86656-111">`ICorDebugProcess5::EnableNGenPolicy` Yöntemi, işlem kullanım ömrü süresince herhangi bir zamanda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="86656-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="86656-112">İlke İlkesi ayarlandıktan sonra yüklü olan tüm modülleri için etkindir.</span><span class="sxs-lookup"><span data-stu-id="86656-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86656-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86656-113">Requirements</span></span>  
 <span data-ttu-id="86656-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86656-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86656-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86656-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86656-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86656-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86656-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86656-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86656-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86656-118">See Also</span></span>  
 [<span data-ttu-id="86656-119">Icordebugprocess5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="86656-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="86656-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86656-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="86656-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="86656-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
