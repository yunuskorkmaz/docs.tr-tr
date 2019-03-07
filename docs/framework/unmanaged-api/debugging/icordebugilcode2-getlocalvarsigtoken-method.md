---
title: ICorDebugILCode2::GetLocalVarSigToken Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee067faddf7300512387c26ae4ce4fda2b73353
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475807"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="a45e0-102">ICorDebugILCode2::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="a45e0-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="a45e0-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="a45e0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a45e0-104">Meta veriler için bu örneği tarafından temsil edilen işlev için yerel değişken imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a45e0-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a45e0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a45e0-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a45e0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a45e0-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="a45e0-107">[out] Bir işaretçi `mdSignature` bu işlev için yerel değişken imzası için belirteç veya `mdSignatureNil` olup olmadığını hiç imza (diğer bir deyişle, işlev herhangi bir yerel değişkeni yoksa).</span><span class="sxs-lookup"><span data-stu-id="a45e0-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a45e0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a45e0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a45e0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a45e0-109">Requirements</span></span>  
 <span data-ttu-id="a45e0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a45e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a45e0-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a45e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a45e0-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a45e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a45e0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a45e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45e0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a45e0-114">See also</span></span>
- [<span data-ttu-id="a45e0-115">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a45e0-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="a45e0-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a45e0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
