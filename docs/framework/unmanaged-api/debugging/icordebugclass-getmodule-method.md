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
ms.openlocfilehash: 9e96d0d82b08449b4675ec7fd1517317006011ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478342"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="9c448-102">ICorDebugClass::GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c448-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="9c448-103">Bu sınıfı tanımlayan modül alır.</span><span class="sxs-lookup"><span data-stu-id="9c448-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c448-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c448-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c448-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c448-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="9c448-106">[out] Bu sınıf tanımlandığı modülü temsil eden bir Icordebugmodule nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c448-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c448-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c448-107">Requirements</span></span>  
 <span data-ttu-id="9c448-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c448-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c448-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c448-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c448-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c448-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c448-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c448-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
