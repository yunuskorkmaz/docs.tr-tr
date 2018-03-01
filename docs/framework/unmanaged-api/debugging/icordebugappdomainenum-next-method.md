---
title: "ICorDebugAppDomainEnum::Next Yöntemi"
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
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c5b773cf49ed67ce6d5981650f2409f7860391a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="52593-102">ICorDebugAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52593-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="52593-103">Uygulama etki alanları belirtilen sayıda geçerli İmleç konumuna başlangıç koleksiyondan alır.</span><span class="sxs-lookup"><span data-stu-id="52593-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52593-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52593-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52593-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52593-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="52593-106">[in] Alınacak uygulama etki alanları sayısı.</span><span class="sxs-lookup"><span data-stu-id="52593-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="52593-107">[out] Her biri uygulama etki alanını temsil eden bir Icordebugappdomain nesneye işaret eden bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52593-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="52593-108">[out] Uygulama etki alanları gerçekte döndürülen sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="52593-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="52593-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="52593-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52593-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52593-110">Requirements</span></span>  
 <span data-ttu-id="52593-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52593-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52593-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52593-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52593-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52593-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52593-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52593-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
