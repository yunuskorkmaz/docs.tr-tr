---
title: ICLRDomainManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129336"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="0f92f-102">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f92f-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="0f92f-103">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f92f-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f92f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0f92f-104">Methods</span></span>  
  
|<span data-ttu-id="0f92f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0f92f-105">Method</span></span>|<span data-ttu-id="0f92f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f92f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f92f-107">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f92f-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="0f92f-108">Varsayılan uygulama etki alanını başlatmak için kullanılacak olan uygulama etki alanı yöneticisinin <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfından türetilen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f92f-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="0f92f-109">SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f92f-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="0f92f-110">Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f92f-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f92f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f92f-111">Remarks</span></span>  
 <span data-ttu-id="0f92f-112">Bu arabirimin bir örneğini almak için, yönetici türü IID `IID_ICLRDomainManager`[ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="0f92f-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f92f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f92f-113">Requirements</span></span>  
 <span data-ttu-id="0f92f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f92f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f92f-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0f92f-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0f92f-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0f92f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f92f-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f92f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f92f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f92f-118">See also</span></span>

- [<span data-ttu-id="0f92f-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f92f-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0f92f-120">Barındırma</span><span class="sxs-lookup"><span data-stu-id="0f92f-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
