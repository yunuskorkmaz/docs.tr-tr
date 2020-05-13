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
ms.openlocfilehash: 3b9c2f0e20488826aca202b3ef454104964b8bb9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210351"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="517c0-102">ICorDebugILCode2::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="517c0-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="517c0-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="517c0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="517c0-104">Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="517c0-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="517c0-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="517c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="517c0-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="517c0-107">dışı `mdSignature`Bu işlev için yerel değişken imzasının belirtecine yönelik bir işaretçi veya `mdSignatureNil` imza yoksa (işlev herhangi bir yerel değişken içermiyorsa).</span><span class="sxs-lookup"><span data-stu-id="517c0-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="517c0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="517c0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="517c0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="517c0-109">Requirements</span></span>  
 <span data-ttu-id="517c0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="517c0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="517c0-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="517c0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="517c0-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="517c0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="517c0-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="517c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517c0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="517c0-114">See also</span></span>

- [<span data-ttu-id="517c0-115">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="517c0-115">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="517c0-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="517c0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
