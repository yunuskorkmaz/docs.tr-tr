---
title: <add> / <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151161"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="fe927-102">\<add> / \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="fe927-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="fe927-103">Bu öğe, belirli bir taşımanın türünü tanımlayan bir anahtar/değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="fe927-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fe927-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe927-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe927-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe927-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fe927-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe927-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe927-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe927-107">Attributes</span></span>  
  
|<span data-ttu-id="fe927-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe927-108">Attribute</span></span>|<span data-ttu-id="fe927-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe927-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe927-110">name</span><span class="sxs-lookup"><span data-stu-id="fe927-110">name</span></span>|<span data-ttu-id="fe927-111">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fe927-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="fe927-112">, Aktarım türünü benzersiz bir şekilde tanımlayan Kullanıcı tanımlı bir anahtar içerir.</span><span class="sxs-lookup"><span data-stu-id="fe927-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="fe927-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="fe927-113">transportConfigurationType</span></span>|<span data-ttu-id="fe927-114">Belirli bir taşımayı uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fe927-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe927-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe927-115">Child Elements</span></span>  

 <span data-ttu-id="fe927-116">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fe927-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe927-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe927-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fe927-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe927-118">Element</span></span>|<span data-ttu-id="fe927-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe927-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="fe927-120">Belirli bir aktarımı uygulayan türlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fe927-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe927-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe927-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="fe927-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe927-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="fe927-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="fe927-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
