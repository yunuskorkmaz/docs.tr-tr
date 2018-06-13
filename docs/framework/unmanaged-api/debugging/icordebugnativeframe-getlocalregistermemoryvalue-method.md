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
ms.openlocfilehash: 5605f7b2ad9ba42a340906559838de22ac79f789
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416686"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a><span data-ttu-id="4627c-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Metodu</span><span class="sxs-lookup"><span data-stu-id="4627c-102">ICorDebugNativeFrame::GetLocalRegisterMemoryValue Method</span></span>
<span data-ttu-id="4627c-103">Bir bağımsız değişken veya biri Düşük word ve yüksek word bellek konumunda depolanan ve kayıt, sırasıyla, bu yerel çerçevesi için belirlenen yerel değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="4627c-103">Gets the value of an argument or local variable, of which the low word and high word are stored in the memory location and specified register, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4627c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4627c-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4627c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4627c-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="4627c-106">[in] Değerin yüksek sözcüğünü içeren kayıt belirtir "CorDebugRegister" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="4627c-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordAddress`  
 <span data-ttu-id="4627c-107">[in] A `CORDB_ADDRESS` değerinin düşük sözcüğünü içeren bellek konumunu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="4627c-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4627c-108">[in] Tarafından başvurulan ikili meta verileri imza boyutu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4627c-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4627c-109">[in] A `PCCOR_SIGNATURE` değerinin türü ikili meta verileri imza gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="4627c-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4627c-110">[out] Belirtilen kayıt ve bellek konumda depolanır alınan değeri temsil eden bir "ICorDebugValue" nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4627c-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4627c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4627c-111">Requirements</span></span>  
 <span data-ttu-id="4627c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4627c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4627c-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4627c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4627c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4627c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4627c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4627c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4627c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4627c-116">See Also</span></span>  
 
