---
title: ICorDebugModule::GetProcess Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff7c77a27e9be58e9702c3a5e3f990863dc83901
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763631"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="09056-102">ICorDebugModule::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="09056-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="09056-103">Bu modül içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="09056-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09056-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09056-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09056-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09056-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="09056-106">[out] Bu modül içeren işlemini temsil eden bir Icordebugprocess nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="09056-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09056-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09056-107">Requirements</span></span>  
 <span data-ttu-id="09056-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09056-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09056-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09056-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09056-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09056-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09056-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09056-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
