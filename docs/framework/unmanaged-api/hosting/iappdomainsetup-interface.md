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
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126868"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="27810-102">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27810-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="27810-103">Konak oluşturmak için [ICorRuntimeHost:: CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metodunu çağırmadan önce konağın bir <xref:System.AppDomain?displayProperty=nameWithType> türü yapılandırmasına izin veren özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="27810-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="27810-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="27810-104">Properties</span></span>  
  
|<span data-ttu-id="27810-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="27810-105">Property</span></span>|<span data-ttu-id="27810-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27810-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="27810-107">Uygulamayı içeren dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="27810-108">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="27810-109">Dosyaların gölge kopyalandığı uygulamaya özgü bir alanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="27810-110">Bir uygulama için yapılandırma dosyasının adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="27810-111">Dinamik olarak oluşturulan dosyaların depolandığı ve eriştiği dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="27810-112">Bu etki alanıyla ilişkili lisans dosyasının yolunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="27810-113">Özel derlemeler için araştırmanın <xref:System.AppDomainSetup.ApplicationBase%2A> diziniyle birleştirilmiş dizinlerin listesini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="27810-114">Uygulamanın arama yolundan <xref:System.AppDomainSetup.ApplicationBase%2A> içeren veya dışlayan bir dize değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="27810-115">Gölge kopya oluşturulacak derlemeleri içeren dizinlerin adlarını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="27810-116">Gölge kopyalamanın açık veya kapalı olup olmadığını gösteren bir dize alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="27810-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="27810-117">Geçerli değerler "true" veya "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="27810-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27810-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27810-118">Remarks</span></span>  
 <span data-ttu-id="27810-119">`IAppDomainSetup` arabirimi, <xref:System.AppDomainSetup> türünün uyguladığı yönetilen <xref:System.IAppDomainSetup> arabirimine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="27810-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="27810-120">Özelliklerinin ayrıntılı açıklamaları için bkz. <xref:System.IAppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27810-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="27810-121">`IAppDomainSetup`, oluşturma işleminden önce bir <xref:System.AppDomain> örneğine eklenebilen derleme bağlama bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="27810-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="27810-122">Örneğin, bir ana bilgisayar, yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları olan kök dizin oluşturmak için <xref:System.AppDomainSetup.ApplicationBase%2A> özelliğini ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="27810-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27810-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27810-123">Requirements</span></span>  
 <span data-ttu-id="27810-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27810-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27810-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27810-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27810-126">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="27810-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27810-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27810-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27810-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27810-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="27810-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27810-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
