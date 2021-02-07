---
description: ': ICorDebugNativeFrame:: GetLocalRegisterMemoryValue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 36cf4d38c65e233a8be91a1e2aeca01ea009f340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729191"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="b59b1-103">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b59b1-103">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>

<span data-ttu-id="b59b1-104">Bir bağımsız değişkenin veya yerel değişkenin değerini alır; bu, alt sözcük ve üst sözcük, bu yerel çerçeve için sırasıyla bellek konumunda ve belirtilen yazmaç üzerinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="b59b1-104">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b59b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b59b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b59b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b59b1-106">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="b59b1-107">'ndaki Değerin yüksek sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="b59b1-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="b59b1-108">'ndaki `CORDB_ADDRESS` Değerin düşük sözcüğünü içeren bellek konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b59b1-108">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b59b1-109">'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b59b1-109">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b59b1-110">'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="b59b1-110">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b59b1-111">dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b59b1-111">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b59b1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b59b1-112">Requirements</span></span>  

 <span data-ttu-id="b59b1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b59b1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b59b1-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b59b1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b59b1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b59b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b59b1-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b59b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59b1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b59b1-117">See also</span></span>
