---
title: ICorDebugILFrame::EnumerateArguments Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d7fb1de0b2ea63c1a766023b23acc42e027af8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475664"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="81831-102">ICorDebugILFrame::EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81831-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="81831-103">Bir numaralandırıcı bu çerçeveye bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="81831-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81831-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81831-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81831-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81831-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="81831-106">[out] Numaralandırıcı bağımsız değişkenlerin Bu çerçevede Icordebugvalueenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81831-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81831-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81831-107">Remarks</span></span>  
 <span data-ttu-id="81831-108">`EnumerateArguments` bağımsız değişkenler bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevede kullanılabilir listeleyen bir numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="81831-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="81831-109">Bu liste olan bağımsız değişkenler içerir [vararg](/cpp/windows/vararg) (diğer bir deyişle, değişken sayıda bağımsız değişkenler) olmayan bağımsız değişkenleri yanı sıra `vararg`.</span><span class="sxs-lookup"><span data-stu-id="81831-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81831-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81831-110">Requirements</span></span>  
 <span data-ttu-id="81831-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81831-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81831-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81831-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81831-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81831-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81831-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81831-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
