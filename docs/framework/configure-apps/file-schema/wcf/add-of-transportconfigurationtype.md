---
title: <add> / <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850311"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="c55b2-102">\<add> / \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="c55b2-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="c55b2-103">Bu öğe, belirli bir taşımanın türünü tanımlayan bir anahtar/değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="c55b2-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c55b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c55b2-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c55b2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55b2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c55b2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c55b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c55b2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c55b2-107">Attributes</span></span>  
  
|<span data-ttu-id="c55b2-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c55b2-108">Attribute</span></span>|<span data-ttu-id="c55b2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c55b2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c55b2-110">name</span><span class="sxs-lookup"><span data-stu-id="c55b2-110">name</span></span>|<span data-ttu-id="c55b2-111">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c55b2-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="c55b2-112">, Aktarım türünü benzersiz bir şekilde tanımlayan Kullanıcı tanımlı bir anahtar içerir.</span><span class="sxs-lookup"><span data-stu-id="c55b2-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="c55b2-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c55b2-113">transportConfigurationType</span></span>|<span data-ttu-id="c55b2-114">Belirli bir taşımayı uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c55b2-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c55b2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55b2-115">Child Elements</span></span>  
 <span data-ttu-id="c55b2-116">Yok</span><span class="sxs-lookup"><span data-stu-id="c55b2-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c55b2-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c55b2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c55b2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c55b2-118">Element</span></span>|<span data-ttu-id="c55b2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c55b2-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="c55b2-120">Belirli bir aktarımı uygulayan türlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c55b2-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c55b2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c55b2-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="c55b2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c55b2-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="c55b2-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="c55b2-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
