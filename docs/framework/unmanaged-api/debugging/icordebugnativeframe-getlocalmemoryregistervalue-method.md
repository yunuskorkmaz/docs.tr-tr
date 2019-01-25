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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c36e9e38acf1d183bcc5af5284e194c994c16749
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706715"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="b276b-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu</span><span class="sxs-lookup"><span data-stu-id="b276b-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="b276b-103">Bir bağımsız değişken veya hangi Düşük word ve yüksek word belirtilen kayıt ve bellek konumu, sırasıyla bu yerel çerçeve için depolanır, yerel bir değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b276b-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b276b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b276b-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b276b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b276b-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="b276b-106">[in] A `CORDB_ADDRESS` değerinin yüksek sözcüğünü içeren bellek konumu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b276b-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="b276b-107">[in] "CorDebugRegister" numaralandırma değerinin düşük sözcüğünü içeren kayıt belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b276b-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b276b-108">[in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b276b-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b276b-109">[in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="b276b-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b276b-110">[out] Belirtilen kayıt ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b276b-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b276b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b276b-111">Requirements</span></span>  
 <span data-ttu-id="b276b-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b276b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b276b-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b276b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b276b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b276b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b276b-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b276b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b276b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b276b-116">See also</span></span>

