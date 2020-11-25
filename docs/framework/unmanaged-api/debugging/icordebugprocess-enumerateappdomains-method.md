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
ms.openlocfilehash: 408658a0abcba9daf4c3046476e21fd4325c7144
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695146"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="7a350-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a350-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>

<span data-ttu-id="7a350-103">Bu işlemdeki tüm uygulama etki alanlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7a350-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a350-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7a350-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a350-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a350-105">Parameters</span></span>  

 `ppAppDomains`  
 <span data-ttu-id="7a350-106">dışı Bu işlemdeki uygulama etki alanları için bir Numaralandırıcı olan [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7a350-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a350-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a350-107">Remarks</span></span>  

 <span data-ttu-id="7a350-108">Bu yöntem [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a350-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a350-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a350-109">Requirements</span></span>  

 <span data-ttu-id="7a350-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a350-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a350-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a350-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a350-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7a350-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a350-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a350-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
