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
ms.openlocfilehash: c8b01ec217fc1b6b91ccf36c8667922b57f26852
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185593"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="a4bb2-102">\<system.web> Öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="a4bb2-102">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="a4bb2-103">ASP.NET barındırma katmanının işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="a4bb2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4bb2-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4bb2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4bb2-105">Attributes and Elements</span></span>  

<span data-ttu-id="a4bb2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4bb2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4bb2-107">Attributes</span></span>  

<span data-ttu-id="a4bb2-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4bb2-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4bb2-109">Child Elements</span></span>  
  
|<span data-ttu-id="a4bb2-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4bb2-110">Element</span></span>|<span data-ttu-id="a4bb2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4bb2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="a4bb2-112">Bir aspnet.config dosyasındaki IIS uygulama havuzlarının yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4bb2-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4bb2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a4bb2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4bb2-114">Element</span></span>|<span data-ttu-id="a4bb2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4bb2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="a4bb2-116">Ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan her yapılandırma dosyasında kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4bb2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4bb2-117">Remarks</span></span>  

<span data-ttu-id="a4bb2-118">`system.web`Öğesi ve onun alt `applicationPool` öğesi .NET Framework 3,5 SP1 itibariyle .NET Framework eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="a4bb2-119">IIS 7,0 veya sonraki sürümlerini tümleşik modda çalıştırdığınızda, bu öğe birleşimi ASP.NET 'in iş parçacıklarını nasıl yönettiğini ve ASP.NET 'in bir IIS uygulama havuzunda barındırıldığında istekleri nasıl sıraya yazacağını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="a4bb2-120">IIS 7,0 veya sonraki sürümlerini klasik veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4bb2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4bb2-121">Example</span></span>  

<span data-ttu-id="a4bb2-122">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığı zaman aspnet.config dosyasında ASP.NET işlem genelinde davranışın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="a4bb2-123">Örnekte IIS 'nin tümleşik modda çalıştığı ve uygulamanın .NET Framework 3,5 SP1 veya sonraki bir sürümü kullanıldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="a4bb2-124">Bu davranış, .NET Framework .NET Framework 3,5 SP1 'den önceki sürümlerinde oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="a4bb2-125">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="a4bb2-126">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="a4bb2-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4bb2-127">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a4bb2-127">Namespace</span></span>||  
|<span data-ttu-id="a4bb2-128">Şema adı</span><span class="sxs-lookup"><span data-stu-id="a4bb2-128">Schema Name</span></span>||  
|<span data-ttu-id="a4bb2-129">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="a4bb2-129">Validation File</span></span>||  
|<span data-ttu-id="a4bb2-130">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="a4bb2-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="a4bb2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4bb2-131">See also</span></span>

- [<span data-ttu-id="a4bb2-132">\<applicationPool> Öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="a4bb2-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
