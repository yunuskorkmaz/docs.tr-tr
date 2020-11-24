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
ms.openlocfilehash: a5abb601fe795a0c615403eec69f68ad9f66f00f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681177"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="165ab-102">ICLRDomainManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="165ab-102">ICLRDomainManager Interface</span></span>

<span data-ttu-id="165ab-103">Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="165ab-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="165ab-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="165ab-104">Methods</span></span>  
  
|<span data-ttu-id="165ab-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="165ab-105">Method</span></span>|<span data-ttu-id="165ab-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="165ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="165ab-107">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="165ab-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="165ab-108"><xref:System.AppDomainManager?displayProperty=nameWithType>Varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisinin sınıfından türetilen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="165ab-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="165ab-109">SetPropertiesForDefaultAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="165ab-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="165ab-110">Varsayılan uygulama etki alanını başlatmak için kullanılacak özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="165ab-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="165ab-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="165ab-111">Remarks</span></span>  

 <span data-ttu-id="165ab-112">Bu arabirimin bir örneğini almak için, yönetici türü IID ile [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırın `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="165ab-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165ab-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="165ab-113">Requirements</span></span>  

 <span data-ttu-id="165ab-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="165ab-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="165ab-115">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="165ab-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="165ab-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="165ab-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="165ab-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="165ab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165ab-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="165ab-118">See also</span></span>

- [<span data-ttu-id="165ab-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="165ab-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="165ab-120">Hosting</span><span class="sxs-lookup"><span data-stu-id="165ab-120">Hosting</span></span>](index.md)
