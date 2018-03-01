---
title: ICorDebugModule::GetSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9474b48526e2ba6292c28e5e66eb97f8e57f2a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="d0e17-102">ICorDebugModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="d0e17-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="d0e17-103">Modül bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="d0e17-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e17-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0e17-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0e17-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0e17-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="d0e17-106">[out] Modül bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0e17-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="d0e17-107">Modülün yerel Görüntü Oluşturucu (NGen.exe) oluşturduysa modül boyutu sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d0e17-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e17-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0e17-108">Requirements</span></span>  
 <span data-ttu-id="d0e17-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0e17-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e17-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0e17-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0e17-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0e17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0e17-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
