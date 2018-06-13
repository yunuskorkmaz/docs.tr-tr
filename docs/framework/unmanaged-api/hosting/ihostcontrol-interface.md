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
ms.openlocfilehash: 961f166cdb2c69e29fef4753a37edcc57c427257
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438096"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="17711-102">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17711-102">IHostControl Interface</span></span>
<span data-ttu-id="17711-103">Derlemeleri yükleme yapılandırma ve ana bilgisayar destekler hangi barındırma arabirimleri belirlemek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="17711-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17711-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="17711-104">Methods</span></span>  
  
|<span data-ttu-id="17711-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="17711-105">Method</span></span>|<span data-ttu-id="17711-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17711-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17711-107">GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17711-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="17711-108">Arabirim işaretçisi arabirimi ana bilgisayarın uygulaması için belirtilen alır `IID`.</span><span class="sxs-lookup"><span data-stu-id="17711-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="17711-109">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17711-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="17711-110">Ana uygulama etki alanı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="17711-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17711-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17711-111">Requirements</span></span>  
 <span data-ttu-id="17711-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17711-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17711-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17711-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17711-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="17711-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17711-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17711-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17711-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17711-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="17711-117">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17711-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="17711-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17711-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="17711-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17711-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
