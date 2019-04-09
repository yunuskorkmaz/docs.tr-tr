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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26cd30be591c4167fa6a6e4d19ba9d1c909c6428
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145775"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="ffcaf-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffcaf-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="ffcaf-103">Bir bağımsız değişken veya yerel değişken biri yüksek word ve Düşük word bellek konumunda depolanan ve kayıt, sırasıyla bu yerel çerçeve için belirtilen değeri alır.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffcaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffcaf-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffcaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffcaf-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="ffcaf-106">[in] "CorDebugRegister" numaralandırma değeri yüksek sözcüğünü içeren kayıt belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="ffcaf-107">[in] A `CORDB_ADDRESS` değerinin düşük sözcüğünü içeren bellek konumu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ffcaf-108">[in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ffcaf-109">[in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ffcaf-110">[out] Belirtilen kayıt ve bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffcaf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffcaf-111">Requirements</span></span>  
 <span data-ttu-id="ffcaf-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffcaf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffcaf-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffcaf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffcaf-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffcaf-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ffcaf-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ffcaf-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ffcaf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcaf-116">See also</span></span>
