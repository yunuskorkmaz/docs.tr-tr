---
title: "ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.LocksHeldByLogicalThread
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82fa031e4842d81f7ddec3e7eeb64c9d7b02e566
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="dc512-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc512-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="dc512-103">Geçerli iş parçacığının tutan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="dc512-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="dc512-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="dc512-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc512-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc512-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc512-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc512-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="dc512-107">[out] Geçerli iş parçacığının tutan kilit sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc512-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc512-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc512-108">Requirements</span></span>  
 <span data-ttu-id="dc512-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc512-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc512-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc512-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc512-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dc512-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc512-112">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="dc512-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc512-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc512-113">See Also</span></span>  
 [<span data-ttu-id="dc512-114">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc512-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
