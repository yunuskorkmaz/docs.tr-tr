---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa9e168b36c8408583ca23dee070fc36b2cb076c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573000"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="f5fba-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Metodu</span><span class="sxs-lookup"><span data-stu-id="f5fba-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="f5fba-103">Bir bağımsız değişken veya yerel değişken biri yüksek word ve Düşük word bellek konumunda depolanan ve kayıt, sırasıyla bu yerel çerçeve için belirtilen değeri alır.</span><span class="sxs-lookup"><span data-stu-id="f5fba-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5fba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5fba-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5fba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5fba-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="f5fba-106">[in] "CorDebugRegister" numaralandırma değeri yüksek sözcüğünü içeren kayıt belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f5fba-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="f5fba-107">[in] A `CORDB_ADDRESS` değerinin düşük sözcüğünü içeren bellek konumu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f5fba-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f5fba-108">[in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f5fba-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f5fba-109">[in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="f5fba-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f5fba-110">[out] Belirtilen kayıt ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5fba-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5fba-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5fba-111">Requirements</span></span>  
 <span data-ttu-id="f5fba-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5fba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fba-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5fba-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5fba-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5fba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5fba-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5fba-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5fba-116">See also</span></span>

