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
ms.openlocfilehash: 97cecd66462cf6a88012b13dec82dbf617891dd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988006"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="8914d-102">ICorDebugModule::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="8914d-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="8914d-103">Bu modül içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="8914d-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8914d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8914d-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8914d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8914d-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="8914d-106">[out] Bu modül içeren işlemini temsil eden bir Icordebugprocess nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8914d-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8914d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8914d-107">Requirements</span></span>  
 <span data-ttu-id="8914d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8914d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8914d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8914d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8914d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8914d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8914d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8914d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
