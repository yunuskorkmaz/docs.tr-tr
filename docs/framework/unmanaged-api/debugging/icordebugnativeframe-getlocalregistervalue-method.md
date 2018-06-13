---
title: ICorDebugNativeFrame::GetLocalRegisterValue Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b408654f367bc846dc878fb8412eb3e896dd192a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417092"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="1eb28-102">ICorDebugNativeFrame::GetLocalRegisterValue Metodu</span><span class="sxs-lookup"><span data-stu-id="1eb28-102">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>
<span data-ttu-id="1eb28-103">Bir bağımsız değişken veya bu yerel çerçeve belirtilen kaydolun depolanan yerel değişken değerini alır.</span><span class="sxs-lookup"><span data-stu-id="1eb28-103">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1eb28-104">Syntax</span></span>  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1eb28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1eb28-105">Parameters</span></span>  
 `reg`  
 <span data-ttu-id="1eb28-106">[in] Değerini içeren kayıt belirtir "CorDebugRegister" numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="1eb28-106">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1eb28-107">[in] Tarafından başvurulan ikili meta verileri imza boyutu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1eb28-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1eb28-108">[in] A `PCCOR_SIGNATURE` değerinin türü ikili meta verileri imza gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="1eb28-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1eb28-109">[out] Belirtilen kayıt defterinde depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1eb28-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1eb28-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1eb28-110">Remarks</span></span>  
 <span data-ttu-id="1eb28-111">`GetLocalRegisterValue` Yöntemi kullanılabilir yerel bir çerçeve veya bir tam zamanında (JIT)-çerçeve derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="1eb28-111">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb28-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1eb28-112">Requirements</span></span>  
 <span data-ttu-id="1eb28-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb28-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb28-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eb28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eb28-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eb28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eb28-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eb28-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1eb28-117">See Also</span></span>  
 
