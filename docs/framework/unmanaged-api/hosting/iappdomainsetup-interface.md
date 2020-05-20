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
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617067"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="9a7fb-102">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a7fb-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="9a7fb-103">Konağın, <xref:System.AppDomain?displayProperty=nameWithType> kendisini oluşturmak Için [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md) metodunu çağırmadan önce bir tür yapılandırmasına izin veren özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9a7fb-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9a7fb-104">Properties</span></span>  
  
|<span data-ttu-id="9a7fb-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="9a7fb-105">Property</span></span>|<span data-ttu-id="9a7fb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a7fb-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="9a7fb-107">Uygulamayı içeren dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="9a7fb-108">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="9a7fb-109">Dosyaların gölge kopyalandığı uygulamaya özgü bir alanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="9a7fb-110">Bir uygulama için yapılandırma dosyasının adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="9a7fb-111">Dinamik olarak oluşturulan dosyaların depolandığı ve eriştiği dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="9a7fb-112">Bu etki alanıyla ilişkili lisans dosyasının yolunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="9a7fb-113">Özel derlemeler için araştırmanın diziniyle birlikte birleştirilmiş dizinlerin listesini alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="9a7fb-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="9a7fb-114">Uygulamanın arama yolundan dahil edilen veya hariç olmayan bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="9a7fb-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="9a7fb-115">Gölge kopya oluşturulacak derlemeleri içeren dizinlerin adlarını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="9a7fb-116">Gölge kopyalamanın açık veya kapalı olup olmadığını gösteren bir dize alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="9a7fb-117">Geçerli değerler "true" veya "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a7fb-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a7fb-118">Remarks</span></span>  
 <span data-ttu-id="9a7fb-119">`IAppDomainSetup`Arabirim, <xref:System.IAppDomainSetup> türün uyguladığı yönetilen arabirime karşılık gelir <xref:System.AppDomainSetup> .</span><span class="sxs-lookup"><span data-stu-id="9a7fb-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="9a7fb-120"><xref:System.IAppDomainSetup?displayProperty=nameWithType>Özelliklerinin ayrıntılı açıklamaları için bkz..</span><span class="sxs-lookup"><span data-stu-id="9a7fb-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="9a7fb-121">`IAppDomainSetup`oluşturma işleminden önce bir örneğe eklenebilen derleme bağlama bilgilerini temsil eder <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="9a7fb-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="9a7fb-122">Örneğin, bir ana bilgisayar, <xref:System.AppDomainSetup.ApplicationBase%2A> yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları olan kök dizin oluşturmak için özelliğini ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7fb-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a7fb-123">Requirements</span></span>  
 <span data-ttu-id="9a7fb-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a7fb-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7fb-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a7fb-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a7fb-126">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9a7fb-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a7fb-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a7fb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7fb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a7fb-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="9a7fb-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a7fb-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
