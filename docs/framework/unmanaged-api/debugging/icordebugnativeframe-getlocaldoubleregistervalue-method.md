---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9de77f942a1b89b0ab11ef71229e491a5305cafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420758"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="90ca8-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Metodu</span><span class="sxs-lookup"><span data-stu-id="90ca8-102">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>
<span data-ttu-id="90ca8-103">Bir bağımsız değişken veya bu yerel çerçeve için iki belirtilen kaydeder depolanan yerel değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="90ca8-103">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ca8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90ca8-104">Syntax</span></span>  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90ca8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90ca8-105">Parameters</span></span>  
 `highWordReg`  
 <span data-ttu-id="90ca8-106">[in] Değerin yüksek sözcüğünü içeren kayıt belirtir "CorDebugRegister" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="90ca8-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="90ca8-107">[in] Değerini `CorDebugRegister` değerinin düşük sözcüğünü içeren kayıt belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="90ca8-107">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="90ca8-108">[in] Tarafından başvurulan ikili meta verileri imza boyutu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="90ca8-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="90ca8-109">[in] A `PCCOR_SIGNATURE` değerinin türü ikili meta verileri imza gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="90ca8-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="90ca8-110">[out] Belirtilen kasalar depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="90ca8-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90ca8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90ca8-111">Remarks</span></span>  
 <span data-ttu-id="90ca8-112">`GetLocalDoubleRegisterValue` Yöntemi kullanılabilir yerel bir çerçeve veya bir tam zamanında (JIT)-çerçeve derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="90ca8-112">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ca8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90ca8-113">Requirements</span></span>  
 <span data-ttu-id="90ca8-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ca8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ca8-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90ca8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90ca8-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ca8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90ca8-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ca8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ca8-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90ca8-118">See Also</span></span>  
 
