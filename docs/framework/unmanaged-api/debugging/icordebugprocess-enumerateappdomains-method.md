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
ms.openlocfilehash: 35e3e37b1487b5dda9945402c6a3338384147f9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792635"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="1621a-102">ICorDebugProcess::EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1621a-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="1621a-103">Bu işlemdeki tüm uygulama etki alanlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1621a-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1621a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1621a-104">Syntax</span></span>  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1621a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1621a-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="1621a-106">dışı Bu işlemdeki uygulama etki alanları için bir Numaralandırıcı olan [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1621a-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1621a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1621a-107">Remarks</span></span>  
 <span data-ttu-id="1621a-108">Bu yöntem [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırmadan önce kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1621a-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1621a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1621a-109">Requirements</span></span>  
 <span data-ttu-id="1621a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1621a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1621a-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1621a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1621a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1621a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1621a-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1621a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
