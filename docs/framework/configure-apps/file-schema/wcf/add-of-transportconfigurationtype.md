---
title: <add> / <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 483ede53df13c896b88171910031dbe9793d66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920041"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="278ef-102">\<\<TransportConfigurationType > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="278ef-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="278ef-103">Bu öğe, belirli bir taşımanın türünü tanımlayan bir anahtar/değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="278ef-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="278ef-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="278ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="278ef-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="278ef-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="278ef-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="278ef-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="278ef-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="278ef-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278ef-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="278ef-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="278ef-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="278ef-109">Attributes and Elements</span></span>  
 <span data-ttu-id="278ef-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="278ef-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="278ef-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="278ef-111">Attributes</span></span>  
  
|<span data-ttu-id="278ef-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="278ef-112">Attribute</span></span>|<span data-ttu-id="278ef-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278ef-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="278ef-114">name</span><span class="sxs-lookup"><span data-stu-id="278ef-114">name</span></span>|<span data-ttu-id="278ef-115">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="278ef-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="278ef-116">, Aktarım türünü benzersiz bir şekilde tanımlayan Kullanıcı tanımlı bir anahtar içerir.</span><span class="sxs-lookup"><span data-stu-id="278ef-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="278ef-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="278ef-117">transportConfigurationType</span></span>|<span data-ttu-id="278ef-118">Belirli bir taşımayı uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="278ef-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="278ef-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="278ef-119">Child Elements</span></span>  
 <span data-ttu-id="278ef-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="278ef-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="278ef-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="278ef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="278ef-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="278ef-122">Element</span></span>|<span data-ttu-id="278ef-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278ef-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278ef-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="278ef-124">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="278ef-125">Belirli bir aktarımı uygulayan türlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="278ef-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="278ef-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="278ef-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="278ef-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="278ef-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="278ef-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="278ef-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
