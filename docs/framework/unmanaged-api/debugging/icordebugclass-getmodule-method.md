---
title: ICorDebugClass::GetModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: e95d10512da73d9f483b87557fd7cd4574503c70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728467"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="9af28-102">ICorDebugClass::GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9af28-102">ICorDebugClass::GetModule Method</span></span>

<span data-ttu-id="9af28-103">Bu sınıfı tanımlayan modülü alır.</span><span class="sxs-lookup"><span data-stu-id="9af28-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af28-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9af28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9af28-105">Parameters</span></span>  

 `pModule`  
 <span data-ttu-id="9af28-106">dışı Bu sınıfın tanımlandığı modülü temsil eden bir ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9af28-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af28-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9af28-107">Requirements</span></span>  

 <span data-ttu-id="9af28-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af28-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af28-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9af28-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9af28-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9af28-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9af28-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af28-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
