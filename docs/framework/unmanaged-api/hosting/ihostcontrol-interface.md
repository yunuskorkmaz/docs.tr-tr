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
ms.openlocfilehash: 1bffef31702aa051d9ca865b18a67ac90c00cd00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680670"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="0bf82-102">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0bf82-102">IHostControl Interface</span></span>

<span data-ttu-id="0bf82-103">Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bf82-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bf82-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0bf82-104">Methods</span></span>  
  
|<span data-ttu-id="0bf82-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0bf82-105">Method</span></span>|<span data-ttu-id="0bf82-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bf82-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bf82-107">GetHostManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0bf82-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="0bf82-108">Konağın, belirtilen arabirim uygulamasına yönelik bir arabirim işaretçisini alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="0bf82-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="0bf82-109">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0bf82-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="0bf82-110">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0bf82-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bf82-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bf82-111">Requirements</span></span>  

 <span data-ttu-id="0bf82-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bf82-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf82-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0bf82-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bf82-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0bf82-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bf82-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf82-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf82-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bf82-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="0bf82-117">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0bf82-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="0bf82-118">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0bf82-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="0bf82-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0bf82-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
