---
description: ': ICorDebugNativeFrame:: GetLocalRegisterValue yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi
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
ms.openlocfilehash: ae21134db11c4d0449ed5f6d583f435a259b83fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729165"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="acdc2-103">ICorDebugNativeFrame::GetLocalRegisterValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acdc2-103">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>

<span data-ttu-id="acdc2-104">Bu yerel çerçeve için belirtilen kasada depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="acdc2-104">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acdc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acdc2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acdc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acdc2-106">Parameters</span></span>  

 `reg`  
 <span data-ttu-id="acdc2-107">'ndaki Değeri içeren kaydı belirten "CorDebugRegister" numaralandırmasının değeri.</span><span class="sxs-lookup"><span data-stu-id="acdc2-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="acdc2-108">'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="acdc2-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="acdc2-109">'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="acdc2-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="acdc2-110">dışı Belirtilen kasada depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="acdc2-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acdc2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acdc2-111">Remarks</span></span>  

 <span data-ttu-id="acdc2-112">`GetLocalRegisterValue`Yöntemi yerel bir çerçevede veya bir tam zamanında (JIT) derlenmiş çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acdc2-112">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acdc2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acdc2-113">Requirements</span></span>  

 <span data-ttu-id="acdc2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acdc2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acdc2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acdc2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acdc2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acdc2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acdc2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acdc2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acdc2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acdc2-118">See also</span></span>
