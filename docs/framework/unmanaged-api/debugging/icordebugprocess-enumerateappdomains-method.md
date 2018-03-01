---
title: "ICorDebugProcess::EnumerateAppDomains Yöntemi"
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
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ba0f554a4ddf52b7c4ced1658055c4370f112ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="ef256-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef256-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="ef256-103">Bu işlem tüm uygulama etki alanları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="ef256-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef256-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef256-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef256-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef256-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="ef256-106">[out] Adresine bir işaretçi bir [Icordebugappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) bu süreçte uygulama etki alanları için başka bir deyişle bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="ef256-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef256-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef256-107">Remarks</span></span>  
 <span data-ttu-id="ef256-108">Bu yöntem, önce kullanılabilir [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ef256-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef256-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef256-109">Requirements</span></span>  
 <span data-ttu-id="ef256-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef256-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef256-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef256-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef256-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef256-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef256-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef256-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
