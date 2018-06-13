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
ms.openlocfilehash: add7239feb1cf6dab0fabe12e178336921211190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414212"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="428d9-102">ICorDebugModule::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="428d9-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="428d9-103">Bu modül içeren işlemini alır.</span><span class="sxs-lookup"><span data-stu-id="428d9-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="428d9-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="428d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="428d9-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="428d9-106">[out] Bu modül içeren işlemi temsil eden Icordebugprocess nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="428d9-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428d9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="428d9-107">Requirements</span></span>  
 <span data-ttu-id="428d9-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="428d9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="428d9-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="428d9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="428d9-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="428d9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="428d9-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="428d9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
