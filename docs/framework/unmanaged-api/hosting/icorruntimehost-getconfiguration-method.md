---
title: ICorRuntimeHost::GetConfiguration Metodu
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f435fc71c3b1eb610b57b60a71819a0f835d4189
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466446"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="321dc-102">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="321dc-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="321dc-103">Ortak dil çalışma zamanı (CLR) geri çağırma yapılandırmasını belirtmek konak izin veren bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="321dc-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="321dc-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="321dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="321dc-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="321dc-106">[out] Adresine bir işaretçi bir [Icorconfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) CLR yapılandırmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="321dc-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321dc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="321dc-107">Remarks</span></span>  
 <span data-ttu-id="321dc-108">CLR başlatılmasını önce yapılandırılması gerekir; Aksi takdirde `GetConfiguration` yöntemi belirten bir hata HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="321dc-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321dc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="321dc-109">Requirements</span></span>  
 <span data-ttu-id="321dc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321dc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321dc-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="321dc-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="321dc-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="321dc-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="321dc-113">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="321dc-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321dc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="321dc-114">See also</span></span>
- [<span data-ttu-id="321dc-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="321dc-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
