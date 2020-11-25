---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: 15485ac94ed9074baacc4fd2662a04bdcefcf1e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709329"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="f9652-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu</span><span class="sxs-lookup"><span data-stu-id="f9652-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>

<span data-ttu-id="f9652-103">Bir bağımsız değişkenin veya yerel değişkenin değerini alır, bu yerel çerçeve için sırasıyla alt sözcük ve yüksek sözcük belirtilen yazmaç ve bellek konumunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="f9652-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9652-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9652-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9652-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9652-105">Parameters</span></span>  

 `highWordAddress`  
 <span data-ttu-id="f9652-106">'ndaki `CORDB_ADDRESS` Değerin yüksek sözcüğünü içeren bellek konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f9652-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="f9652-107">'ndaki Değerin düşük sözcüğünü içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="f9652-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f9652-108">'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="f9652-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f9652-109">'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="f9652-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f9652-110">dışı Belirtilen yazmaç ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9652-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9652-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9652-111">Requirements</span></span>  

 <span data-ttu-id="f9652-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9652-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9652-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9652-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9652-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9652-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9652-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9652-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9652-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9652-116">See also</span></span>
