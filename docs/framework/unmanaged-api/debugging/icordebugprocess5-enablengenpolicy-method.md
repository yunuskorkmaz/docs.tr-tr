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
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731395"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="3c84b-102">ICorDebugProcess5::EnableNGENPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c84b-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="3c84b-103">Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3c84b-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c84b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3c84b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c84b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c84b-105">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="3c84b-106">'ndaki Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir [Cordebugger Gngenpolicy](cordebugngenpolicy-enumeration.md) sabiti.</span><span class="sxs-lookup"><span data-stu-id="3c84b-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c84b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c84b-107">Remarks</span></span>  

 <span data-ttu-id="3c84b-108">İlke başarıyla ayarlandıysa, yöntemi döndürür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="3c84b-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="3c84b-109">, `ePolicy` [Corspergngenpolicy](cordebugngenpolicy-enumeration.md)tarafından tanımlanan numaralandırılmış değerler aralığının dışındaysa, yöntemi döner `E_INVALIDARG` ve yöntem çağrısının etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="3c84b-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="3c84b-110">Yerel Görüntü Oluşturucu (Ngen.exe) ilkesi güncelleştirilemeyebilir, yöntemi döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="3c84b-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="3c84b-111">`ICorDebugProcess5::EnableNGenPolicy`Yöntemi, işlemin kullanım ömrü boyunca herhangi bir zamanda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3c84b-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="3c84b-112">İlke, ilke ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="3c84b-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c84b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c84b-113">Requirements</span></span>  

 <span data-ttu-id="3c84b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c84b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c84b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3c84b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c84b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3c84b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c84b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c84b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c84b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c84b-118">See also</span></span>

- [<span data-ttu-id="3c84b-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c84b-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3c84b-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c84b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3c84b-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3c84b-121">Debugging</span></span>](index.md)
