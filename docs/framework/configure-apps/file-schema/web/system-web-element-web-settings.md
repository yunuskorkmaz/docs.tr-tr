---
description: 'Hakkında daha fazla bilgi edinin: <System. Web> öğesi (Web ayarları)'
title: <system.web> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 2adcd3eba1eb6d67bcb4dc82243cd70d31d64fe9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681909"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="45234-103">\<system.web> Öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="45234-103">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="45234-104">ASP.NET barındırma katmanının işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="45234-104">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="45234-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="45234-105">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45234-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45234-106">Attributes and Elements</span></span>  

<span data-ttu-id="45234-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45234-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45234-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45234-108">Attributes</span></span>  

<span data-ttu-id="45234-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="45234-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45234-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45234-110">Child Elements</span></span>  
  
|<span data-ttu-id="45234-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="45234-111">Element</span></span>|<span data-ttu-id="45234-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45234-112">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="45234-113">Bir aspnet.config dosyasındaki IIS uygulama havuzlarının yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45234-113">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45234-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45234-114">Parent Elements</span></span>  
  
|<span data-ttu-id="45234-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="45234-115">Element</span></span>|<span data-ttu-id="45234-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45234-116">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="45234-117">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45234-117">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45234-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45234-118">Remarks</span></span>  

<span data-ttu-id="45234-119">`system.web`Öğesi ve onun alt `applicationPool` öğesi .NET Framework 3,5 SP1 itibariyle .NET Framework eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="45234-119">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="45234-120">IIS 7,0 veya sonraki sürümlerini tümleşik modda çalıştırdığınızda, bu öğe birleşimi ASP.NET 'in iş parçacıklarını nasıl yönettiğini ve ASP.NET 'in bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya yazacağını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="45234-120">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="45234-121">IIS 7,0 veya sonraki sürümlerini klasik veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="45234-121">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45234-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="45234-122">Example</span></span>  

<span data-ttu-id="45234-123">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığı zaman aspnet.config dosyasında ASP.NET işlem genelinde davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45234-123">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="45234-124">Örnekte IIS 'nin tümleşik modda çalıştığı ve uygulamanın .NET Framework 3,5 SP1 veya sonraki bir sürümü kullanıldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="45234-124">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="45234-125">Bu davranış, .NET Framework .NET Framework 3,5 SP1 'den önceki sürümlerinde oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="45234-125">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="45234-126">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="45234-126">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="45234-127">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="45234-127">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45234-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="45234-128">Namespace</span></span>||  
|<span data-ttu-id="45234-129">Şema adı</span><span class="sxs-lookup"><span data-stu-id="45234-129">Schema Name</span></span>||  
|<span data-ttu-id="45234-130">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="45234-130">Validation File</span></span>||  
|<span data-ttu-id="45234-131">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="45234-131">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="45234-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45234-132">See also</span></span>

- [<span data-ttu-id="45234-133">\<applicationPool> Öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="45234-133">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
