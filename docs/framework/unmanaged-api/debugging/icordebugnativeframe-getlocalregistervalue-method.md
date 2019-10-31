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
ms.openlocfilehash: 132e0868426670ba61d8ee12ba7007be1a8a52de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139400"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="5fca3-102">ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fca3-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="5fca3-103">Bu yerel çerçeve için belirtilen kasada depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="5fca3-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fca3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fca3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fca3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fca3-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="5fca3-106">'ndaki Değeri içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="5fca3-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5fca3-107">'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5fca3-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5fca3-108">'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.</span><span class="sxs-lookup"><span data-stu-id="5fca3-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5fca3-109">dışı Belirtilen kasada depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5fca3-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fca3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fca3-110">Remarks</span></span>  
 <span data-ttu-id="5fca3-111">`GetLocalRegisterValue` yöntemi yerel bir çerçevede veya bir tam zamanında (JıT) derlenmiş çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fca3-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fca3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fca3-112">Requirements</span></span>  
 <span data-ttu-id="5fca3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fca3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fca3-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fca3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fca3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5fca3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fca3-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fca3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fca3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fca3-117">See also</span></span>
