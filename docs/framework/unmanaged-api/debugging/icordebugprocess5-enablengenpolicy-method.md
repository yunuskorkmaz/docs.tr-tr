---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: EnableNGENPolicy yöntemi'
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
ms.openlocfilehash: 0f3194893665bfe9fff802a293aaafed8254f2e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649929"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="8db9e-103">ICorDebugProcess5::EnableNGENPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8db9e-103">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="8db9e-104">Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8db9e-104">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8db9e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8db9e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8db9e-106">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="8db9e-107">'ndaki Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir [Cordebugger Gngenpolicy](cordebugngenpolicy-enumeration.md) sabiti.</span><span class="sxs-lookup"><span data-stu-id="8db9e-107">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8db9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8db9e-108">Remarks</span></span>  

 <span data-ttu-id="8db9e-109">İlke başarıyla ayarlandıysa, yöntemi döndürür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="8db9e-109">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="8db9e-110">, `ePolicy` [Corspergngenpolicy](cordebugngenpolicy-enumeration.md)tarafından tanımlanan numaralandırılmış değerler aralığının dışındaysa, yöntemi döner `E_INVALIDARG` ve yöntem çağrısının etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="8db9e-110">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="8db9e-111">Yerel Görüntü Oluşturucu (Ngen.exe) ilkesi güncelleştirilemeyebilir, yöntemi döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="8db9e-111">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="8db9e-112">`ICorDebugProcess5::EnableNGenPolicy`Yöntemi, işlemin kullanım ömrü boyunca herhangi bir zamanda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8db9e-112">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="8db9e-113">İlke, ilke ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="8db9e-113">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db9e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8db9e-114">Requirements</span></span>  

 <span data-ttu-id="8db9e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8db9e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8db9e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8db9e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8db9e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8db9e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8db9e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8db9e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db9e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8db9e-119">See also</span></span>

- [<span data-ttu-id="8db9e-120">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8db9e-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8db9e-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8db9e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8db9e-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8db9e-122">Debugging</span></span>](index.md)
