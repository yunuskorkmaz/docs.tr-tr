---
title: IAppDomainSetup Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9db1b787015231b3d9053d4ed316cb70c5db96ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="cd25a-102">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd25a-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="cd25a-103">Yapılandırmak konak izin verme özellikler sağlayan bir <xref:System.AppDomain?displayProperty=nameWithType> türü çağırmadan önce [Icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cd25a-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd25a-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cd25a-104">Properties</span></span>  
  
|<span data-ttu-id="cd25a-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="cd25a-105">Property</span></span>|<span data-ttu-id="cd25a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd25a-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="cd25a-107">Alır veya uygulamayı içeren dizinin adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="cd25a-108">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="cd25a-109">Alır veya bir alanın adı belirli uygulamaya gölge kopyalanan dosyaların nerede ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="cd25a-110">Alır veya ayarlar uygulamanın yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="cd25a-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="cd25a-111">Alır veya dinamik olarak üretilen dosyaları nerede depolanır ve erişilen dizin adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="cd25a-112">Alır veya bu etki alanı ile ilişkili lisans dosyasının yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="cd25a-113">Alır veya ayarlar ile bir araya dizinler listesinde <xref:System.AppDomainSetup.ApplicationBase%2A> özel derlemeler için araştırma için dizin.</span><span class="sxs-lookup"><span data-stu-id="cd25a-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="cd25a-114">İçerir veya dışlar bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> uygulama için arama yolundan.</span><span class="sxs-lookup"><span data-stu-id="cd25a-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="cd25a-115">Alır veya gölge kopyalar olması için derlemeleri içeren dizin adlarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd25a-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="cd25a-116">Alır veya ayarlar gölge kopyalama veya açık olup olmadığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="cd25a-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="cd25a-117">Geçerli değerler "true" veya "false".</span><span class="sxs-lookup"><span data-stu-id="cd25a-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd25a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd25a-118">Remarks</span></span>  
 <span data-ttu-id="cd25a-119">`IAppDomainSetup` Arabirimi karşılık gelen yönetilen <xref:System.IAppDomainSetup> arabirim, hangi <xref:System.AppDomainSetup> yazın uygular.</span><span class="sxs-lookup"><span data-stu-id="cd25a-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="cd25a-120">Bkz: <xref:System.IAppDomainSetup?displayProperty=nameWithType> özelliklerini ayrıntılı açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="cd25a-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="cd25a-121">`IAppDomainSetup`eklenebilir derleme bağlama bilgilerini temsil eden bir <xref:System.AppDomain> örneği oluşturulduktan önce.</span><span class="sxs-lookup"><span data-stu-id="cd25a-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="cd25a-122">Örneğin, bir ana bilgisayar ayarlayabilirsiniz <xref:System.AppDomainSetup.ApplicationBase%2A> Yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları bir kök dizin oluşturmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="cd25a-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd25a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd25a-123">Requirements</span></span>  
 <span data-ttu-id="cd25a-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd25a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd25a-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd25a-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd25a-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cd25a-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd25a-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd25a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd25a-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd25a-128">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [<span data-ttu-id="cd25a-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd25a-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
