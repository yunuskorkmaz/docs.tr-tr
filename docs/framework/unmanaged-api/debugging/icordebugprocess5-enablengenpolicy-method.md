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
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792459"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="4b0b1-102">ICorDebugProcess5::EnableNGENPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b0b1-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="4b0b1-103">Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b0b1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b0b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b0b1-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="4b0b1-106">'ndaki Bir uygulamanın yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri nasıl yüklediğini belirleyen bir [Cordebugger Gngenpolicy](cordebugngenpolicy-enumeration.md) sabiti.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b0b1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b0b1-107">Remarks</span></span>  
 <span data-ttu-id="4b0b1-108">İlke başarıyla ayarlandıysa, yöntem `S_OK`döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="4b0b1-109">`ePolicy`, [cormısgngenpolicy](cordebugngenpolicy-enumeration.md)tarafından tanımlanan numaralandırılmış değerler aralığının dışındaysa, yöntemi `E_INVALIDARG` döndürür ve yöntem çağrısının etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="4b0b1-110">Yerel Görüntü Oluşturucu (Ngen. exe) ilkesi güncelleştirilemeyebilir, yöntem `E_FAIL`döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="4b0b1-111">`ICorDebugProcess5::EnableNGenPolicy` yöntemi, işlemin kullanım ömrü boyunca herhangi bir zamanda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="4b0b1-112">İlke, ilke ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b0b1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b0b1-113">Requirements</span></span>  
 <span data-ttu-id="4b0b1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b0b1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0b1-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b0b1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b0b1-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4b0b1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b0b1-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b0b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0b1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b0b1-118">See also</span></span>

- [<span data-ttu-id="4b0b1-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b0b1-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="4b0b1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b0b1-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4b0b1-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4b0b1-121">Debugging</span></span>](index.md)
