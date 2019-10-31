---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: d44d7c23f88f5ea93f608d06b69f69b2c3637b5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096839"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="991a3-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="991a3-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="991a3-103">Bir bağımsız değişkenin veya yerel değişkenin değerini alır; bu, alt sözcük ve üst sözcük, bu yerel çerçeve için sırasıyla bellek konumunda ve belirtilen yazmaç üzerinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="991a3-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="991a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="991a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="991a3-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="991a3-106">'ndaki Değerin yüksek sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="991a3-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="991a3-107">'ndaki Değerin düşük sözcüğünü içeren bellek konumunu belirten bir `CORDB_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="991a3-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="991a3-108">'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="991a3-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="991a3-109">'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.</span><span class="sxs-lookup"><span data-stu-id="991a3-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="991a3-110">dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="991a3-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="991a3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="991a3-111">Requirements</span></span>  
 <span data-ttu-id="991a3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991a3-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="991a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="991a3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="991a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="991a3-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991a3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="991a3-116">See also</span></span>
