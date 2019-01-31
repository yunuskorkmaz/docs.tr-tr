---
title: <add> , <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 84ad745e7789fc2de8dcc23f3607b63702af05a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263463"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="3cfac-102">\<Ekle >, \<transportConfigurationType ></span><span class="sxs-lookup"><span data-stu-id="3cfac-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="3cfac-103">Belirli bir türünü tanımlayan bir anahtar/değer çifti öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3cfac-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="3cfac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3cfac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3cfac-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3cfac-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="3cfac-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="3cfac-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="3cfac-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="3cfac-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cfac-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cfac-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cfac-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cfac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3cfac-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cfac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cfac-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3cfac-111">Attributes</span></span>  
  
|<span data-ttu-id="3cfac-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3cfac-112">Attribute</span></span>|<span data-ttu-id="3cfac-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cfac-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cfac-114">name</span><span class="sxs-lookup"><span data-stu-id="3cfac-114">name</span></span>|<span data-ttu-id="3cfac-115">Dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="3cfac-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="3cfac-116">Aktarım Türü benzersiz olarak tanıtan bir kullanıcı tanımlı bir anahtar içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3cfac-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="3cfac-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="3cfac-117">transportConfigurationType</span></span>|<span data-ttu-id="3cfac-118">Belirli taşıma uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3cfac-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cfac-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cfac-119">Child Elements</span></span>  
 <span data-ttu-id="3cfac-120">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3cfac-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cfac-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3cfac-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3cfac-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="3cfac-122">Element</span></span>|<span data-ttu-id="3cfac-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cfac-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cfac-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="3cfac-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="3cfac-125">Belirli taşıma uygulayan türler koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="3cfac-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3cfac-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cfac-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="3cfac-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="3cfac-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3cfac-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
