---
description: ': ICLRDomainManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d719e89d81e8c7abb1f238ce50b4e236de17ac72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790015"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="fbdd1-103">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fbdd1-103">ICLRDomainManager Interface</span></span>

<span data-ttu-id="fbdd1-104">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbdd1-104">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbdd1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fbdd1-105">Methods</span></span>  
  
|<span data-ttu-id="fbdd1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fbdd1-106">Method</span></span>|<span data-ttu-id="fbdd1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbdd1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbdd1-108">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbdd1-108">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="fbdd1-109"><xref:System.AppDomainManager?displayProperty=nameWithType>Varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbdd1-109">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="fbdd1-110">SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbdd1-110">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="fbdd1-111">Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fbdd1-111">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbdd1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbdd1-112">Remarks</span></span>  

 <span data-ttu-id="fbdd1-113">Bu arabirimin bir örneğini almak için, yönetici türü IID ile [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırın `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="fbdd1-113">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbdd1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbdd1-114">Requirements</span></span>  

 <span data-ttu-id="fbdd1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbdd1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbdd1-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fbdd1-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fbdd1-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fbdd1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbdd1-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbdd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbdd1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbdd1-119">See also</span></span>

- [<span data-ttu-id="fbdd1-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fbdd1-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="fbdd1-121">Hosting</span><span class="sxs-lookup"><span data-stu-id="fbdd1-121">Hosting</span></span>](index.md)
