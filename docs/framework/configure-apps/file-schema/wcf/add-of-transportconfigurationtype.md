---
description: 'Hakkında daha fazla bilgi <add> edinin: <transportConfigurationType>'
title: <add> / <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 4a4a68e1f70bcb2ec7d55d5d6c3b530e71ddc55d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750019"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="c29ca-103">\<add> / \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="c29ca-103">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="c29ca-104">Bu öğe, belirli bir taşımanın türünü tanımlayan bir anahtar/değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="c29ca-104">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c29ca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c29ca-105">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c29ca-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c29ca-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c29ca-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c29ca-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c29ca-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c29ca-108">Attributes</span></span>  
  
|<span data-ttu-id="c29ca-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c29ca-109">Attribute</span></span>|<span data-ttu-id="c29ca-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c29ca-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c29ca-111">name</span><span class="sxs-lookup"><span data-stu-id="c29ca-111">name</span></span>|<span data-ttu-id="c29ca-112">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c29ca-112">Required String attribute.</span></span><br /><br /> <span data-ttu-id="c29ca-113">, Aktarım türünü benzersiz bir şekilde tanımlayan Kullanıcı tanımlı bir anahtar içerir.</span><span class="sxs-lookup"><span data-stu-id="c29ca-113">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="c29ca-114">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c29ca-114">transportConfigurationType</span></span>|<span data-ttu-id="c29ca-115">Belirli bir taşımayı uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c29ca-115">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c29ca-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c29ca-116">Child Elements</span></span>  

 <span data-ttu-id="c29ca-117">Yok</span><span class="sxs-lookup"><span data-stu-id="c29ca-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c29ca-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c29ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c29ca-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c29ca-119">Element</span></span>|<span data-ttu-id="c29ca-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c29ca-120">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="c29ca-121">Belirli bir aktarımı uygulayan türlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c29ca-121">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c29ca-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c29ca-122">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="c29ca-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c29ca-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c29ca-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="c29ca-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
