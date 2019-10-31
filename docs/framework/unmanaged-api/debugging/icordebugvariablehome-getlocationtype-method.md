---
title: 'Icordebugvariablehome:: GetLocationType yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125107"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="d4500-102">Icordebugvariablehome:: GetLocationType yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4500-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="d4500-103">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d4500-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4500-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4500-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4500-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4500-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="d4500-106">dışı Değişkenin yerel konumunun türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4500-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="d4500-107">Daha fazla bilgi için, bkz. [Variablelocationtype](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="d4500-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4500-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4500-108">Requirements</span></span>  
 <span data-ttu-id="d4500-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4500-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4500-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4500-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4500-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d4500-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4500-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4500-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4500-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4500-113">See also</span></span>

- [<span data-ttu-id="d4500-114">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4500-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="d4500-115">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d4500-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
