---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILCode2:: GetLocalVarSigToken yöntemi'
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
ms.openlocfilehash: cdf2725274a132528123534ddd36ae95e265af44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791432"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="df085-103">ICorDebugILCode2::GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="df085-103">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="df085-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="df085-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="df085-105">Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="df085-105">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df085-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df085-106">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df085-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df085-107">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="df085-108">dışı `mdSignature` Bu işlev için yerel değişken imzasının belirtecine yönelik bir işaretçi veya `mdSignatureNil` imza yoksa (işlev herhangi bir yerel değişken içermiyorsa).</span><span class="sxs-lookup"><span data-stu-id="df085-108">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df085-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df085-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df085-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df085-110">Requirements</span></span>  

 <span data-ttu-id="df085-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df085-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df085-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df085-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df085-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df085-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df085-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df085-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df085-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df085-115">See also</span></span>

- [<span data-ttu-id="df085-116">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df085-116">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="df085-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df085-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
