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
ms.openlocfilehash: 5d33c917ab814083ec2f3a3f3de6bdc264d90b77
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791015"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="447b5-102">Icordebugvariablehome:: GetLocationType yöntemi</span><span class="sxs-lookup"><span data-stu-id="447b5-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="447b5-103">Değişkenin yerel konumunun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="447b5-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="447b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="447b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="447b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="447b5-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="447b5-106">dışı Değişkenin yerel konumunun türüne yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="447b5-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="447b5-107">Daha fazla bilgi için, bkz. [Variablelocationtype](variablelocationtype-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="447b5-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="447b5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="447b5-108">Requirements</span></span>  
 <span data-ttu-id="447b5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="447b5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="447b5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="447b5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="447b5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="447b5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="447b5-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="447b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447b5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="447b5-113">See also</span></span>

- [<span data-ttu-id="447b5-114">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="447b5-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="447b5-115">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="447b5-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
