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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436364"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="bf60f-102">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf60f-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="bf60f-103">Varsayılan uygulama etki alanı başlatın ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf60f-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf60f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf60f-104">Methods</span></span>  
  
|<span data-ttu-id="bf60f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bf60f-105">Method</span></span>|<span data-ttu-id="bf60f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf60f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf60f-107">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf60f-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="bf60f-108">Öğesinden türetilen tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılan uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="bf60f-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="bf60f-109">SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf60f-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="bf60f-110">Varsayılan uygulama etki alanı başlatmak için kullanılan özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf60f-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf60f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf60f-111">Remarks</span></span>  
 <span data-ttu-id="bf60f-112">Bu arabirim örneğini almak için arama [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) Yöneticisi türü IID yöntemiyle `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="bf60f-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf60f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf60f-113">Requirements</span></span>  
 <span data-ttu-id="bf60f-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf60f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf60f-115">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bf60f-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bf60f-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bf60f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf60f-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf60f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf60f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf60f-118">See Also</span></span>  
 [<span data-ttu-id="bf60f-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bf60f-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="bf60f-120">Barındırma</span><span class="sxs-lookup"><span data-stu-id="bf60f-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
