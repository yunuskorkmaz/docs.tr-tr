---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: 10f06fb04099ef947711bc7c5641e5a7f1fa36b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695721"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="3f85e-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f85e-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>

<span data-ttu-id="3f85e-103">Bu yerel çerçeve için belirtilen iki kasada depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="3f85e-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f85e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3f85e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f85e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f85e-105">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="3f85e-106">'ndaki Değerin yüksek sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="3f85e-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="3f85e-107">'ndaki `CorDebugRegister` Değerin düşük sözcüğünü içeren kaydı belirten numaralandırmanın değeri.</span><span class="sxs-lookup"><span data-stu-id="3f85e-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3f85e-108">'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3f85e-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3f85e-109">'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="3f85e-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3f85e-110">dışı Belirtilen kayıtlarda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f85e-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f85e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f85e-111">Remarks</span></span>  

 <span data-ttu-id="3f85e-112">`GetLocalDoubleRegisterValue`Yöntemi yerel bir çerçevede veya bir tam zamanında (JIT) derlenmiş çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f85e-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f85e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f85e-113">Requirements</span></span>  

 <span data-ttu-id="3f85e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f85e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f85e-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f85e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f85e-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f85e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f85e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f85e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f85e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f85e-118">See also</span></span>
