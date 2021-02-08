---
description: 'Daha fazla bilgi edinin: IHostControl arabirimi'
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
ms.openlocfilehash: e7a242ed0fdaa734425bec9b48f01fe45cba5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789469"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="1a956-103">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a956-103">IHostControl Interface</span></span>

<span data-ttu-id="1a956-104">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a956-104">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a956-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a956-105">Methods</span></span>  
  
|<span data-ttu-id="1a956-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1a956-106">Method</span></span>|<span data-ttu-id="1a956-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a956-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a956-108">GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a956-108">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="1a956-109">Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="1a956-109">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="1a956-110">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a956-110">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="1a956-111">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1a956-111">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a956-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a956-112">Requirements</span></span>  

 <span data-ttu-id="1a956-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a956-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a956-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a956-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a956-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1a956-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a956-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a956-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a956-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a956-117">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="1a956-118">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a956-118">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="1a956-119">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a956-119">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1a956-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a956-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
