---
title: IHostControl Arabirimi
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 014e5c9951091046ae07374794743e82affcd5ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967745"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="e33aa-102">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e33aa-102">IHostControl Interface</span></span>
<span data-ttu-id="e33aa-103">Derlemeleri yüklenmesini yapılandırma ve ana bilgisayar destekler hangi barındırma arabirimleri belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e33aa-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e33aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e33aa-104">Methods</span></span>  
  
|<span data-ttu-id="e33aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e33aa-105">Method</span></span>|<span data-ttu-id="e33aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e33aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e33aa-107">GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e33aa-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="e33aa-108">Ana bilgisayarın uygulanmasına arabirimi belirtilen bir arabirim işaretçisi alır `IID`.</span><span class="sxs-lookup"><span data-stu-id="e33aa-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="e33aa-109">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e33aa-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="e33aa-110">Konak, bir uygulama etki alanı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e33aa-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e33aa-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e33aa-111">Requirements</span></span>  
 <span data-ttu-id="e33aa-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e33aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e33aa-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e33aa-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e33aa-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e33aa-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e33aa-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e33aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33aa-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e33aa-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="e33aa-117">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e33aa-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="e33aa-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e33aa-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e33aa-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e33aa-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
