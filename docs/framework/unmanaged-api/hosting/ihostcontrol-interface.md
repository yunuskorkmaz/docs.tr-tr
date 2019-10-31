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
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195879"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="a8729-102">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8729-102">IHostControl Interface</span></span>
<span data-ttu-id="a8729-103">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8729-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8729-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8729-104">Methods</span></span>  
  
|<span data-ttu-id="a8729-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a8729-105">Method</span></span>|<span data-ttu-id="a8729-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8729-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8729-107">GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8729-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="a8729-108">Ana bilgisayarın, belirtilen `IID`sahip olduğu arabirim uygulamasına yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a8729-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="a8729-109">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8729-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="a8729-110">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a8729-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8729-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8729-111">Requirements</span></span>  
 <span data-ttu-id="a8729-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8729-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8729-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8729-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8729-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a8729-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8729-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8729-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8729-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8729-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="a8729-117">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8729-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="a8729-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8729-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a8729-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8729-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
