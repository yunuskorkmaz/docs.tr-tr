---
title: ICorDebugBoxValue::GetObject Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30038d383e78c23715b844df0bee7c1124885a69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745215"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="d3496-102">ICorDebugBoxValue::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="d3496-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="d3496-103">Paketlenmiş değer alır.</span><span class="sxs-lookup"><span data-stu-id="d3496-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3496-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3496-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3496-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3496-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="d3496-106">[out] Paketlenmiş değer temsil eden bir Icordebugobjectvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d3496-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3496-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3496-107">Requirements</span></span>  
 <span data-ttu-id="d3496-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3496-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3496-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3496-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3496-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3496-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3496-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3496-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
