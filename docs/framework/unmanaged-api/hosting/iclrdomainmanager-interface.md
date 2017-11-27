---
title: ICLRDomainManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager
helpviewer_keywords: ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75a7e93d26a5c77484d78ad4632bedf8def6a44b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="35e11-102">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35e11-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="35e11-103">Varsayılan uygulama etki alanı başlatın ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="35e11-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35e11-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="35e11-104">Methods</span></span>  
  
|<span data-ttu-id="35e11-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="35e11-105">Method</span></span>|<span data-ttu-id="35e11-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35e11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35e11-107">SetAppDomainManagerType yöntemi</span><span class="sxs-lookup"><span data-stu-id="35e11-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="35e11-108">Öğesinden türetilen tür belirtir <xref:System.AppDomainManager?displayProperty=nameWithType> sınıfının varsayılan uygulama etki alanı başlatmak için kullanılan uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="35e11-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="35e11-109">SetPropertiesForDefaultAppDomain yöntemi</span><span class="sxs-lookup"><span data-stu-id="35e11-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="35e11-110">Varsayılan uygulama etki alanı başlatmak için kullanılan özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="35e11-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35e11-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35e11-111">Remarks</span></span>  
 <span data-ttu-id="35e11-112">Bu arabirim örneğini almak için arama [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) Yöneticisi türü IID yöntemiyle `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="35e11-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e11-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35e11-113">Requirements</span></span>  
 <span data-ttu-id="35e11-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e11-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35e11-115">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="35e11-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="35e11-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="35e11-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35e11-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35e11-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e11-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35e11-118">See Also</span></span>  
 [<span data-ttu-id="35e11-119">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="35e11-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="35e11-120">Barındırma</span><span class="sxs-lookup"><span data-stu-id="35e11-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
