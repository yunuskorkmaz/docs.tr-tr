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
ms.openlocfilehash: b1a044d1600f7e21e3abfbf704daef5213617b4c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780040"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="93ddf-102">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="93ddf-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="93ddf-103">Ortak dil çalışma zamanı (CLR) geri çağırma yapılandırmasını belirtmek konak izin veren bir nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="93ddf-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ddf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93ddf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93ddf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93ddf-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="93ddf-106">[out] Adresine bir işaretçi bir [Icorconfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) CLR yapılandırmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="93ddf-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93ddf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93ddf-107">Remarks</span></span>  
 <span data-ttu-id="93ddf-108">CLR başlatılmasını önce yapılandırılması gerekir; Aksi takdirde `GetConfiguration` yöntemi belirten bir hata HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="93ddf-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ddf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93ddf-109">Requirements</span></span>  
 <span data-ttu-id="93ddf-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93ddf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ddf-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93ddf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93ddf-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="93ddf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93ddf-113">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="93ddf-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ddf-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93ddf-114">See also</span></span>

- [<span data-ttu-id="93ddf-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93ddf-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
