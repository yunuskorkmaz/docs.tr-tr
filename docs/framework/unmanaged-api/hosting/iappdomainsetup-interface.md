---
title: IAppDomainSetup Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainSetup
helpviewer_keywords: IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6ed5ea00799fff70626114257efef2d06b505ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="a10f2-102">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a10f2-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="a10f2-103">Yapılandırmak konak izin verme özellikler sağlayan bir <xref:System.AppDomain?displayProperty=nameWithType> türü çağırmadan önce [Icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a10f2-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a10f2-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a10f2-104">Properties</span></span>  
  
|<span data-ttu-id="a10f2-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="a10f2-105">Property</span></span>|<span data-ttu-id="a10f2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a10f2-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="a10f2-107">Alır veya uygulamayı içeren dizinin adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="a10f2-108">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="a10f2-109">Alır veya bir alanın adı belirli uygulamaya gölge kopyalanan dosyaların nerede ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="a10f2-110">Alır veya ayarlar uygulamanın yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="a10f2-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="a10f2-111">Alır veya dinamik olarak üretilen dosyaları nerede depolanır ve erişilen dizin adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="a10f2-112">Alır veya bu etki alanı ile ilişkili lisans dosyasının yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="a10f2-113">Alır veya ayarlar ile bir araya dizinler listesinde <xref:System.AppDomainSetup.ApplicationBase%2A> özel derlemeler için araştırma için dizin.</span><span class="sxs-lookup"><span data-stu-id="a10f2-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="a10f2-114">İçerir veya dışlar bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> uygulama için arama yolundan.</span><span class="sxs-lookup"><span data-stu-id="a10f2-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="a10f2-115">Alır veya gölge kopyalar olması için derlemeleri içeren dizin adlarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a10f2-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="a10f2-116">Alır veya ayarlar gölge kopyalama veya açık olup olmadığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a10f2-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="a10f2-117">Geçerli değerler "true" veya "false".</span><span class="sxs-lookup"><span data-stu-id="a10f2-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a10f2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a10f2-118">Remarks</span></span>  
 <span data-ttu-id="a10f2-119">`IAppDomainSetup` Arabirimi karşılık gelen yönetilen <xref:System.IAppDomainSetup> arabirim, hangi <xref:System.AppDomainSetup> yazın uygular.</span><span class="sxs-lookup"><span data-stu-id="a10f2-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="a10f2-120">Bkz: <xref:System.IAppDomainSetup?displayProperty=nameWithType> özelliklerini ayrıntılı açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="a10f2-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="a10f2-121">`IAppDomainSetup`eklenebilir derleme bağlama bilgilerini temsil eden bir <xref:System.AppDomain> örneği oluşturulduktan önce.</span><span class="sxs-lookup"><span data-stu-id="a10f2-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="a10f2-122">Örneğin, bir ana bilgisayar ayarlayabilirsiniz <xref:System.AppDomainSetup.ApplicationBase%2A> Yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları bir kök dizin oluşturmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="a10f2-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a10f2-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a10f2-123">Requirements</span></span>  
 <span data-ttu-id="a10f2-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10f2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10f2-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a10f2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a10f2-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a10f2-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a10f2-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10f2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10f2-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a10f2-128">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [<span data-ttu-id="a10f2-129">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a10f2-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
