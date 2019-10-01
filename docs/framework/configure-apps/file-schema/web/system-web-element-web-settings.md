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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699098"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="d7787-102">@no__t -0system. Web > öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="d7787-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="d7787-103">ASP.NET barındırma katmanının işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d7787-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="d7787-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="d7787-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d7787-105">&nbsp; @ no__t-1 **@no__t -3system. web >**</span><span class="sxs-lookup"><span data-stu-id="d7787-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7787-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7787-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7787-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7787-107">Attributes and Elements</span></span>  

<span data-ttu-id="d7787-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7787-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7787-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7787-109">Attributes</span></span>  

<span data-ttu-id="d7787-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7787-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7787-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7787-111">Child Elements</span></span>  
  
|<span data-ttu-id="d7787-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7787-112">Element</span></span>|<span data-ttu-id="d7787-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7787-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7787-114">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="d7787-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="d7787-115">ASPNET. config dosyasındaki IIS uygulama havuzlarının yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7787-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7787-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7787-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d7787-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7787-117">Element</span></span>|<span data-ttu-id="d7787-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7787-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7787-119">\<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d7787-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="d7787-120">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7787-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7787-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7787-121">Remarks</span></span>  

<span data-ttu-id="d7787-122">@No__t-0 öğesi ve onun alt `applicationPool` öğesi .NET Framework 3,5 SP1 itibariyle .NET Framework eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7787-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="d7787-123">IIS 7,0 veya sonraki sürümlerini tümleşik modda çalıştırdığınızda, bu öğe birleşimi ASP.NET 'in iş parçacıklarını nasıl yönettiğini ve ASP.NET 'in bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya yazacağını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d7787-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="d7787-124">IIS 7,0 veya sonraki sürümlerini klasik veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d7787-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7787-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7787-125">Example</span></span>  

<span data-ttu-id="d7787-126">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında Aspnet. config dosyasında ASP.NET işlem genelindeki davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7787-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="d7787-127">Örnekte IIS 'nin tümleşik modda çalıştığı ve uygulamanın .NET Framework 3,5 SP1 veya sonraki bir sürümü kullanıldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d7787-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="d7787-128">Bu davranış, .NET Framework .NET Framework 3,5 SP1 'den önceki sürümlerinde oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="d7787-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="d7787-129">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="d7787-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="d7787-130">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="d7787-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7787-131">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d7787-131">Namespace</span></span>||  
|<span data-ttu-id="d7787-132">Şema adı</span><span class="sxs-lookup"><span data-stu-id="d7787-132">Schema Name</span></span>||  
|<span data-ttu-id="d7787-133">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="d7787-133">Validation File</span></span>||  
|<span data-ttu-id="d7787-134">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="d7787-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d7787-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7787-135">See also</span></span>

- [<span data-ttu-id="d7787-136">\<applicationPool > öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="d7787-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
