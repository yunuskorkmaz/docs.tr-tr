---
title: IAppDomainSetup Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220077"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="4a721-102">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a721-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="4a721-103">Yapılandırmak konak izin verme özellikleri sağlar bir <xref:System.AppDomain?displayProperty=nameWithType> çağırmadan önce türü [Icorruntimehost::createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a721-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4a721-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4a721-104">Properties</span></span>  
  
|<span data-ttu-id="4a721-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="4a721-105">Property</span></span>|<span data-ttu-id="4a721-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a721-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="4a721-107">Alır veya ayarlar uygulamasını içeren dizinin adı.</span><span class="sxs-lookup"><span data-stu-id="4a721-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="4a721-108">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a721-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="4a721-109">Alır veya bir alanın adını belirli uygulamayı gölge kopyalanan dosyaların nerede ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a721-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="4a721-110">Alır veya bir uygulama yapılandırma dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a721-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="4a721-111">Alır veya ayarlar dinamik olarak oluşturulan dosyaların nerede depolanır ve erişilebilir bir dizinin adı.</span><span class="sxs-lookup"><span data-stu-id="4a721-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="4a721-112">Alır ya da bu etki alanı ile ilişkili lisans dosyasının yolunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a721-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="4a721-113">Alır veya birlikte dizinler listesini ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> özel derlemeler için araştırma için dizin.</span><span class="sxs-lookup"><span data-stu-id="4a721-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="4a721-114">İçerir veya dışlar bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> uygulama için arama yolu.</span><span class="sxs-lookup"><span data-stu-id="4a721-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="4a721-115">Alır veya gölge kopyalar derlemeler içeren dizin adlarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a721-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="4a721-116">Alır veya ayarlar gölge kopyalama hakkında açık olup olmadığını gösteren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a721-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="4a721-117">Geçerli değerler "true" veya "false".</span><span class="sxs-lookup"><span data-stu-id="4a721-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a721-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a721-118">Remarks</span></span>  
 <span data-ttu-id="4a721-119">`IAppDomainSetup` Arabirimi karşılık gelen yönetilen <xref:System.IAppDomainSetup> arabirim, hangi <xref:System.AppDomainSetup> yazın uygular.</span><span class="sxs-lookup"><span data-stu-id="4a721-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="4a721-120">Bkz: <xref:System.IAppDomainSetup?displayProperty=nameWithType> özelliklerini ayrıntılı açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="4a721-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 `IAppDomainSetup` <span data-ttu-id="4a721-121">eklenebilir derleme bağlama bilgilerini temsil eden bir <xref:System.AppDomain> örneği oluşturulduktan önce.</span><span class="sxs-lookup"><span data-stu-id="4a721-121">represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="4a721-122">Örneğin, bir konak ayarlayabilirsiniz <xref:System.AppDomainSetup.ApplicationBase%2A> Yönetilen derlemeler için ortak dil çalışma zamanı (CLR) araştırmalarını bir kök dizin oluşturmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="4a721-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a721-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a721-123">Requirements</span></span>  
 <span data-ttu-id="4a721-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a721-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a721-125">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a721-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a721-126">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a721-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4a721-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4a721-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a721-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a721-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="4a721-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a721-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
