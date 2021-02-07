---
description: ': ICorDebugProcess:: Enumerateappdomain metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d212fafe7ae1355ba69e07b88c3b96119371fe43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691529"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="c9b1e-103">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9b1e-103">ICorDebugProcess::EnumerateAppDomains Method</span></span>

<span data-ttu-id="c9b1e-104">Bu işlemdeki tüm uygulama etki alanlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c9b1e-104">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b1e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9b1e-105">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9b1e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9b1e-106">Parameters</span></span>  

 `ppAppDomains`  
 <span data-ttu-id="c9b1e-107">dışı Bu işlemdeki uygulama etki alanları için bir Numaralandırıcı olan [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9b1e-107">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9b1e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9b1e-108">Remarks</span></span>  

 <span data-ttu-id="c9b1e-109">Bu yöntem [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9b1e-109">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b1e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9b1e-110">Requirements</span></span>  

 <span data-ttu-id="c9b1e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b1e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b1e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9b1e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9b1e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9b1e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9b1e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b1e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
