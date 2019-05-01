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
ms.openlocfilehash: ce53149b92ca40ad50ecbefaf4701940e8567ae5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984756"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="90864-102">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90864-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="90864-103">Varsayılan uygulama etki alanı başlatmak ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="90864-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90864-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="90864-104">Methods</span></span>  
  
|<span data-ttu-id="90864-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="90864-105">Method</span></span>|<span data-ttu-id="90864-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90864-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90864-107">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90864-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="90864-108">Türetilmiş tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılacak uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="90864-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="90864-109">SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90864-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="90864-110">Varsayılan uygulama etki alanı başlatmak için kullanılacak özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="90864-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90864-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90864-111">Remarks</span></span>  
 <span data-ttu-id="90864-112">Bu arabirim örneğini almak için arama [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) Yöneticisi türü IID yöntemiyle `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="90864-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90864-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90864-113">Requirements</span></span>  
 <span data-ttu-id="90864-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90864-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90864-115">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="90864-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="90864-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="90864-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90864-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90864-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90864-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90864-118">See also</span></span>

- [<span data-ttu-id="90864-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="90864-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="90864-120">Barındırma</span><span class="sxs-lookup"><span data-stu-id="90864-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
