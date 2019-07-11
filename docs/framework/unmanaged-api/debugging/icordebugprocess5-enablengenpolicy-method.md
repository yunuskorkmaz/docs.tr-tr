---
title: ICorDebugProcess5::EnableNGENPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38ff08fa7e7db986006c4e0e09b1ac9cf1be801e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767153"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="81788-102">ICorDebugProcess5::EnableNGENPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81788-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="81788-103">Nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81788-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81788-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81788-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81788-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81788-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="81788-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen sabiti.</span><span class="sxs-lookup"><span data-stu-id="81788-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81788-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81788-107">Remarks</span></span>  
 <span data-ttu-id="81788-108">İlke başarıyla olarak ayarlanırsa, yöntem döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="81788-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="81788-109">Varsa `ePolicy` tarafından tanımlanan Enum değerleri aralığı dışında [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), yöntemi döndürür `E_INVALIDARG` ve yöntem çağrısının hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="81788-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="81788-110">Native Image Generator (Ngen.exe) ilkesi güncelleştirilemiyor ise, yöntem döndürür `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="81788-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="81788-111">`ICorDebugProcess5::EnableNGenPolicy` İşlem ömrü boyunca herhangi bir zamanda yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="81788-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="81788-112">İlke, ilkeyi ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="81788-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81788-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81788-113">Requirements</span></span>  
 <span data-ttu-id="81788-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81788-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81788-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81788-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81788-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81788-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81788-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81788-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81788-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81788-118">See also</span></span>

- [<span data-ttu-id="81788-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81788-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="81788-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="81788-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="81788-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="81788-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
