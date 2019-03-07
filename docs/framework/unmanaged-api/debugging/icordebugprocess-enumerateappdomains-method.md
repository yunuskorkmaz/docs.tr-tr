---
title: ICorDebugProcess::EnumerateAppDomains Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02e051d311e447475bea724b0bd7420ee8b590f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495734"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="7eb8a-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7eb8a-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="7eb8a-103">Bu işlem tüm uygulama etki alanları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7eb8a-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7eb8a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eb8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7eb8a-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="7eb8a-106">[out] Adresine bir işaretçi bir [Icordebugappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) diğer bir deyişle bu işlemde uygulama etki alanları için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="7eb8a-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eb8a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7eb8a-107">Remarks</span></span>  
 <span data-ttu-id="7eb8a-108">Bu yöntem, önce kullanılabilir [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7eb8a-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb8a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7eb8a-109">Requirements</span></span>  
 <span data-ttu-id="7eb8a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb8a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb8a-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eb8a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eb8a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb8a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb8a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
