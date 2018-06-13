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
ms.openlocfilehash: a1a29840efa173a6546ca00a9dc437e098d6f2aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423396"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="1f987-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f987-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="1f987-103">Bu işlem tüm uygulama etki alanları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1f987-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f987-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f987-104">Syntax</span></span>  
  
```  
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f987-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f987-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="1f987-106">[out] Adresine bir işaretçi bir [Icordebugappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) bu süreçte uygulama etki alanları için başka bir deyişle bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="1f987-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f987-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f987-107">Remarks</span></span>  
 <span data-ttu-id="1f987-108">Bu yöntem, önce kullanılabilir [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f987-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f987-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f987-109">Requirements</span></span>  
 <span data-ttu-id="1f987-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f987-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f987-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f987-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f987-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f987-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f987-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f987-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
