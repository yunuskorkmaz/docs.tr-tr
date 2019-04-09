---
title: <add> , <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: c71a58b13e89bedb5eed24d784c82fb1525f7625
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126730"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="640fc-102">\<Ekle >, \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="640fc-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="640fc-103">Belirli bir türünü tanımlayan bir anahtar/değer çifti öğesidir.</span><span class="sxs-lookup"><span data-stu-id="640fc-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="640fc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="640fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="640fc-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="640fc-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="640fc-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="640fc-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="640fc-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="640fc-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640fc-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="640fc-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="640fc-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="640fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="640fc-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="640fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="640fc-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="640fc-111">Attributes</span></span>  
  
|<span data-ttu-id="640fc-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="640fc-112">Attribute</span></span>|<span data-ttu-id="640fc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="640fc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="640fc-114">name</span><span class="sxs-lookup"><span data-stu-id="640fc-114">name</span></span>|<span data-ttu-id="640fc-115">Dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="640fc-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="640fc-116">Aktarım Türü benzersiz olarak tanıtan bir kullanıcı tanımlı bir anahtar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="640fc-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="640fc-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="640fc-117">transportConfigurationType</span></span>|<span data-ttu-id="640fc-118">Belirli taşıma uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="640fc-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="640fc-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="640fc-119">Child Elements</span></span>  
 <span data-ttu-id="640fc-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="640fc-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="640fc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="640fc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="640fc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="640fc-122">Element</span></span>|<span data-ttu-id="640fc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="640fc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="640fc-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="640fc-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="640fc-125">Belirli taşıma uygulayan türler koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="640fc-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="640fc-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="640fc-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="640fc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640fc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="640fc-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="640fc-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
