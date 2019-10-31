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
ms.openlocfilehash: cee095003c136142052b8f946fa8227927c80ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096875"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="b8505-102">ICorDebugNativeFrame::GetLocalMemoryValue Metodu</span><span class="sxs-lookup"><span data-stu-id="b8505-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="b8505-103">Bu yerel çerçeve için belirtilen bellek konumunda depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b8505-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8505-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8505-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8505-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8505-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b8505-106">'ndaki Değeri içeren bellek konumunu belirten bir `CORDB_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="b8505-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b8505-107">'ndaki `pvSigBlob` parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b8505-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b8505-108">'ndaki Değerin türünün ikili meta veri imzasına işaret eden bir `PCCOR_SIGNATURE` değeri.</span><span class="sxs-lookup"><span data-stu-id="b8505-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b8505-109">dışı Belirtilen bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8505-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8505-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8505-110">Requirements</span></span>  
 <span data-ttu-id="b8505-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8505-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8505-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8505-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8505-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8505-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8505-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8505-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8505-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8505-115">See also</span></span>
