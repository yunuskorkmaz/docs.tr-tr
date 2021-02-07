---
description: ': IAppDomainSetup arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8fd224308ea68f7b56ae174c7f71fc4f89630101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760590"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="19388-103">IAppDomainSetup Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19388-103">IAppDomainSetup Interface</span></span>

<span data-ttu-id="19388-104">Konağın, <xref:System.AppDomain?displayProperty=nameWithType> kendisini oluşturmak Için [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md) metodunu çağırmadan önce bir tür yapılandırmasına izin veren özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="19388-104">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="19388-105">Özellikler</span><span class="sxs-lookup"><span data-stu-id="19388-105">Properties</span></span>  
  
|<span data-ttu-id="19388-106">Özellik</span><span class="sxs-lookup"><span data-stu-id="19388-106">Property</span></span>|<span data-ttu-id="19388-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19388-107">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="19388-108">Uygulamayı içeren dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-108">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="19388-109">Uygulamanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-109">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="19388-110">Dosyaların gölge kopyalandığı uygulamaya özgü bir alanın adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-110">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="19388-111">Bir uygulama için yapılandırma dosyasının adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-111">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="19388-112">Dinamik olarak oluşturulan dosyaların depolandığı ve eriştiği dizinin adını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-112">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="19388-113">Bu etki alanıyla ilişkili lisans dosyasının yolunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-113">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="19388-114">Özel derlemeler için araştırmanın diziniyle birlikte birleştirilmiş dizinlerin listesini alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="19388-114">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="19388-115">Uygulamanın arama yolundan dahil edilen veya hariç olmayan bir dize değeri alır veya ayarlar <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="19388-115">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="19388-116">Gölge kopya oluşturulacak derlemeleri içeren dizinlerin adlarını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-116">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="19388-117">Gölge kopyalamanın açık veya kapalı olup olmadığını gösteren bir dize alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="19388-117">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="19388-118">Geçerli değerler "true" veya "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="19388-118">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19388-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19388-119">Remarks</span></span>  

 <span data-ttu-id="19388-120">`IAppDomainSetup`Arabirim, <xref:System.IAppDomainSetup> türün uyguladığı yönetilen arabirime karşılık gelir <xref:System.AppDomainSetup> .</span><span class="sxs-lookup"><span data-stu-id="19388-120">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="19388-121"><xref:System.IAppDomainSetup?displayProperty=nameWithType>Özelliklerinin ayrıntılı açıklamaları için bkz..</span><span class="sxs-lookup"><span data-stu-id="19388-121">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="19388-122">`IAppDomainSetup` oluşturma işleminden önce bir örneğe eklenebilen derleme bağlama bilgilerini temsil eder <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="19388-122">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="19388-123">Örneğin, bir ana bilgisayar, <xref:System.AppDomainSetup.ApplicationBase%2A> yönetilen derlemeler için ortak dil çalışma zamanı (CLR) yoklamaları olan kök dizin oluşturmak için özelliğini ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="19388-123">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19388-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19388-124">Requirements</span></span>  

 <span data-ttu-id="19388-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19388-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19388-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19388-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19388-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="19388-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19388-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19388-128">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19388-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19388-129">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="19388-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19388-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
