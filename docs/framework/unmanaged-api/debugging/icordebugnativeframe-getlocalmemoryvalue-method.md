---
title: ICorDebugNativeFrame::GetLocalMemoryValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a35072b788321d22cec6de2f05a2863341417dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474767"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="7abb4-102">ICorDebugNativeFrame::GetLocalMemoryValue Metodu</span><span class="sxs-lookup"><span data-stu-id="7abb4-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="7abb4-103">Bir bağımsız değişken veya yerel değişken bu yerel çerçeve için belirtilen bellek konumunda depolanan değeri alır.</span><span class="sxs-lookup"><span data-stu-id="7abb4-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7abb4-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7abb4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7abb4-106">[in] A `CORDB_ADDRESS` değerini içeren bellek konumu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7abb4-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7abb4-107">[in] Tarafından başvurulan ikili meta veri imzası boyutunu belirten bir tamsayı `pvSigBlob` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7abb4-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7abb4-108">[in] A `PCCOR_SIGNATURE` değerin türü. ikili meta verileri imza işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="7abb4-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="7abb4-109">[out] Belirtilen bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7abb4-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abb4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7abb4-110">Requirements</span></span>  
 <span data-ttu-id="7abb4-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abb4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abb4-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7abb4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abb4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7abb4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abb4-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abb4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abb4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7abb4-115">See also</span></span>

