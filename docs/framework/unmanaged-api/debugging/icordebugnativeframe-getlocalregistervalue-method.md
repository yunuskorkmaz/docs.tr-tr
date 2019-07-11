---
title: ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d287305934c7884d5474935e50de3d26e225975
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746156"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="0dcf0-102">ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dcf0-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="0dcf0-103">Bir bağımsız değişken veya yerel bu çerçeve için belirtilen kayıt defterinde depolanan yerel değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dcf0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dcf0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dcf0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dcf0-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="0dcf0-106">[in] "CorDebugRegister" numaralandırma değerini içeren kayıt belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0dcf0-107">[in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0dcf0-108">[in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0dcf0-109">[out] Belirtilen kayıt defterinde depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dcf0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dcf0-110">Remarks</span></span>  
 <span data-ttu-id="0dcf0-111">`GetLocalRegisterValue` Yöntemi, bir yerel çerçeve veya bir tam zamanında (JIT) kullanılabilir-çerçeve derlenir.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dcf0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dcf0-112">Requirements</span></span>  
 <span data-ttu-id="0dcf0-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dcf0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dcf0-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dcf0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dcf0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dcf0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dcf0-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dcf0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dcf0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dcf0-117">See also</span></span>
