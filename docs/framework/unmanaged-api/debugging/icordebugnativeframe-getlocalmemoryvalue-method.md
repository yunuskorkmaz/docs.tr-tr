---
description: ': ICorDebugNativeFrame:: GetLocalMemoryValue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5fbdf9474ca8c5849b7d917ecddff491b329113b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729247"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="c50d1-103">ICorDebugNativeFrame::GetLocalMemoryValue Metodu</span><span class="sxs-lookup"><span data-stu-id="c50d1-103">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>

<span data-ttu-id="c50d1-104">Bu yerel çerçeve için belirtilen bellek konumunda depolanan bir bağımsız değişkenin veya yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c50d1-104">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c50d1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c50d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c50d1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c50d1-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="c50d1-107">'ndaki `CORDB_ADDRESS` Değeri içeren bellek konumunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="c50d1-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c50d1-108">'ndaki Parametresi tarafından başvurulan ikili meta veri imzasının boyutunu belirten bir tamsayı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c50d1-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c50d1-109">'ndaki `PCCOR_SIGNATURE` Değerin türünün ikili meta veri imzasına işaret eden bir değer.</span><span class="sxs-lookup"><span data-stu-id="c50d1-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c50d1-110">dışı Belirtilen bellek konumunda depolanan alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c50d1-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c50d1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c50d1-111">Requirements</span></span>  

 <span data-ttu-id="c50d1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c50d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c50d1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c50d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c50d1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c50d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c50d1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c50d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50d1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c50d1-116">See also</span></span>
