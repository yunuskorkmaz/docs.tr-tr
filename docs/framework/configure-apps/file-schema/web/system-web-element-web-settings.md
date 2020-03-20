---
title: <system.web> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152847"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="6ff2f-102">\<system.web> Element (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6ff2f-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="6ff2f-103">ASP.NET barındırma katmanının işlem genelindeki davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="6ff2f-104">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="6ff2f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6ff2f-105">&nbsp;&nbsp;**\<system.web>**</span><span class="sxs-lookup"><span data-stu-id="6ff2f-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff2f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ff2f-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ff2f-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ff2f-107">Attributes and Elements</span></span>  

<span data-ttu-id="6ff2f-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ff2f-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6ff2f-109">Attributes</span></span>  

<span data-ttu-id="6ff2f-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ff2f-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ff2f-111">Child Elements</span></span>  
  
|<span data-ttu-id="6ff2f-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="6ff2f-112">Element</span></span>|<span data-ttu-id="6ff2f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ff2f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ff2f-114">\<uygulamaHavuz></span><span class="sxs-lookup"><span data-stu-id="6ff2f-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="6ff2f-115">Aspnet.config dosyasında IIS uygulama havuzları için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ff2f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6ff2f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6ff2f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="6ff2f-117">Element</span></span>|<span data-ttu-id="6ff2f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ff2f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ff2f-119">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="6ff2f-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="6ff2f-120">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ff2f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ff2f-121">Remarks</span></span>  

<span data-ttu-id="6ff2f-122">.NET `system.web` Framework `applicationPool` 3.5 SP1 itibariyle eleman ve alt öğesi .NET Çerçevesi'ne eklendi.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="6ff2f-123">Tümleşik modda IIS 7.0 veya daha sonraki sürümleri çalıştırdığınızda, bu öğe birleşimi iş parçacıklarını nasıl ASP.NET ve ASP.NET bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya oluşturduğunu yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="6ff2f-124">Klasik veya ISAPI modunda IIS 7.0 veya daha sonraki sürümleri çalıştırırsanız, bu ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff2f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ff2f-125">Example</span></span>  

<span data-ttu-id="6ff2f-126">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında aspnet.config dosyasındaki işlem genelindeASP.NET davranışın nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="6ff2f-127">Örnek, IIS'nin Tümleşik modda çalıştığını ve uygulamanın .NET Framework 3.5 SP1 veya daha sonraki bir sürümü kullandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="6ff2f-128">Bu davranış.NET Framework 3.5 SP1'den önceki .NET Framework sürümlerinde oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="6ff2f-129">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="6ff2f-130">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="6ff2f-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ff2f-131">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6ff2f-131">Namespace</span></span>||  
|<span data-ttu-id="6ff2f-132">Şema Adı</span><span class="sxs-lookup"><span data-stu-id="6ff2f-132">Schema Name</span></span>||  
|<span data-ttu-id="6ff2f-133">Doğrulama Dosyası</span><span class="sxs-lookup"><span data-stu-id="6ff2f-133">Validation File</span></span>||  
|<span data-ttu-id="6ff2f-134">Boş Olabilir</span><span class="sxs-lookup"><span data-stu-id="6ff2f-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="6ff2f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff2f-135">See also</span></span>

- [<span data-ttu-id="6ff2f-136">\<applicationPool> Elemanı (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6ff2f-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
