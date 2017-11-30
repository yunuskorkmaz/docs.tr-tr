---
title: ICorDebugILCode2::GetLocalVarSigToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d41b60e5fb528dfba0f7fa82d7792a1f08ba915
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="8eef5-102">ICorDebugILCode2::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="8eef5-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="8eef5-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="8eef5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8eef5-104">Meta veriler bu örneği tarafından temsil edilen işlevi için yerel değişken İmza belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="8eef5-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eef5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eef5-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8eef5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8eef5-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="8eef5-107">[out] Bir işaretçi `mdSignature` bu işlev için yerel değişken imza için belirteç veya `mdSignatureNil` olup olmadığını hiç imza (diğer bir deyişle, işlev yerel değişkenlerin yoksa).</span><span class="sxs-lookup"><span data-stu-id="8eef5-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eef5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eef5-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eef5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eef5-109">Requirements</span></span>  
 <span data-ttu-id="8eef5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eef5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eef5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eef5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eef5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eef5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eef5-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eef5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eef5-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8eef5-114">See Also</span></span>  
 [<span data-ttu-id="8eef5-115">Icordebugılcode2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eef5-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="8eef5-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8eef5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
