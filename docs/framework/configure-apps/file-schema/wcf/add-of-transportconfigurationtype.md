---
title: <add> / <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850311"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="f457b-102">\<\<TransportConfigurationType > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="f457b-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="f457b-103">Bu öğe, belirli bir taşımanın türünü tanımlayan bir anahtar/değer çiftidir.</span><span class="sxs-lookup"><span data-stu-id="f457b-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="f457b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f457b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f457b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f457b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f457b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="f457b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="f457b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<transportConfigurationTypes >** ](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="f457b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="f457b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="f457b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f457b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f457b-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f457b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f457b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f457b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f457b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f457b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f457b-112">Attributes</span></span>  
  
|<span data-ttu-id="f457b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f457b-113">Attribute</span></span>|<span data-ttu-id="f457b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f457b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f457b-115">name</span><span class="sxs-lookup"><span data-stu-id="f457b-115">name</span></span>|<span data-ttu-id="f457b-116">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f457b-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="f457b-117">, Aktarım türünü benzersiz bir şekilde tanımlayan Kullanıcı tanımlı bir anahtar içerir.</span><span class="sxs-lookup"><span data-stu-id="f457b-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="f457b-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="f457b-118">transportConfigurationType</span></span>|<span data-ttu-id="f457b-119">Belirli bir taşımayı uygulayan türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f457b-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f457b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f457b-120">Child Elements</span></span>  
 <span data-ttu-id="f457b-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="f457b-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f457b-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f457b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f457b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f457b-123">Element</span></span>|<span data-ttu-id="f457b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f457b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f457b-125">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="f457b-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="f457b-126">Belirli bir aktarımı uygulayan türlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f457b-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f457b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="f457b-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="f457b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f457b-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="f457b-129">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f457b-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
