---
title: ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19b3a184272af06e465257d317ab32f5a9c3686a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="6075c-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Metodu</span><span class="sxs-lookup"><span data-stu-id="6075c-102">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>
<span data-ttu-id="6075c-103">Bir bağımsız değişken veya Düşük word ve yüksek word belirtilen YAZMAÇ ve bellek konumuna sırasıyla için bu yerel çerçeve depolandığı yerel değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6075c-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6075c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6075c-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6075c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6075c-105">Parameters</span></span>  
 `highWordAddress`  
 <span data-ttu-id="6075c-106">[in] A `CORDB_ADDRESS` değerinin yüksek sözcüğünü içeren bellek konumunu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6075c-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="6075c-107">[in] Değerin düşük sözcüğünü içeren kayıt belirtir "CorDebugRegister" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="6075c-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6075c-108">[in] Tarafından başvurulan ikili meta verileri imza boyutu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6075c-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6075c-109">[in] A `PCCOR_SIGNATURE` değerinin türü ikili meta verileri imza gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="6075c-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6075c-110">[out] Belirtilen kayıt ve bellek konumda depolanır alınan değeri temsil eden bir "ICorDebugValue" nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6075c-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6075c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6075c-111">Requirements</span></span>  
 <span data-ttu-id="6075c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6075c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6075c-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6075c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6075c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6075c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6075c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6075c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6075c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6075c-116">See Also</span></span>  
 
