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
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139569"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="db021-102">ICorRuntimeHost::GetConfiguration Metodu</span><span class="sxs-lookup"><span data-stu-id="db021-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="db021-103">Konağın ortak dil çalışma zamanının (CLR) geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="db021-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db021-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db021-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db021-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db021-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="db021-106">dışı CLR 'yi yapılandırmak için kullanılabilen [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db021-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db021-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db021-107">Remarks</span></span>  
 <span data-ttu-id="db021-108">CLR 'nin başlatılmasından önce yapılandırılması gerekir; Aksi takdirde `GetConfiguration` yöntemi bir hata belirten HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="db021-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db021-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db021-109">Requirements</span></span>  
 <span data-ttu-id="db021-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db021-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db021-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db021-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db021-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="db021-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db021-113">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="db021-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db021-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db021-114">See also</span></span>

- [<span data-ttu-id="db021-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db021-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
