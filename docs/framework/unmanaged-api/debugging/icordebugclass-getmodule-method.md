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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 205b7670bac55d428d7458b7accaee5e00b00b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745587"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="84348-102">ICorDebugClass::GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84348-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="84348-103">Bu sınıfı tanımlayan modül alır.</span><span class="sxs-lookup"><span data-stu-id="84348-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84348-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84348-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84348-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84348-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="84348-106">[out] Bu sınıf tanımlandığı modülü temsil eden bir Icordebugmodule nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84348-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84348-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84348-107">Requirements</span></span>  
 <span data-ttu-id="84348-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84348-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84348-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84348-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84348-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84348-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84348-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84348-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
