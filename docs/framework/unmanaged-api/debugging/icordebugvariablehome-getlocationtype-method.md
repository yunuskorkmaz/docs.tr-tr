---
description: ': Icordebugvariablehome:: GetLocationType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6efe9c045641d162be820961ca75c21a2b8fc14b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728801"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="cf82b-103">Icordebugvariablehome:: GetLocationType yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf82b-103">ICorDebugVariableHome::GetLocationType Method</span></span>

<span data-ttu-id="cf82b-104">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="cf82b-104">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf82b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf82b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf82b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf82b-106">Parameters</span></span>  

 `pLocationType`  
 <span data-ttu-id="cf82b-107">dışı Değişkenin yerel konumunun türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf82b-107">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="cf82b-108">Daha fazla bilgi için, bkz. [Variablelocationtype](variablelocationtype-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="cf82b-108">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf82b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf82b-109">Requirements</span></span>  

 <span data-ttu-id="cf82b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf82b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf82b-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf82b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf82b-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf82b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf82b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf82b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf82b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf82b-114">See also</span></span>

- [<span data-ttu-id="cf82b-115">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf82b-115">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="cf82b-116">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cf82b-116">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
