---
title: '&lt;transportConfigurationType&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b27994cae77ec012e0b432e702c9c2ccb1933b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="87b38-102">&lt;transportConfigurationType&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="87b38-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="87b38-103">Belirli bir türünü tanımlayan bir anahtar/değer çifti öğedir.</span><span class="sxs-lookup"><span data-stu-id="87b38-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="87b38-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="87b38-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87b38-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="87b38-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="87b38-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="87b38-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="87b38-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="87b38-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b38-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87b38-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87b38-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87b38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="87b38-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87b38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87b38-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87b38-111">Attributes</span></span>  
  
|<span data-ttu-id="87b38-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87b38-112">Attribute</span></span>|<span data-ttu-id="87b38-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87b38-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87b38-114">name</span><span class="sxs-lookup"><span data-stu-id="87b38-114">name</span></span>|<span data-ttu-id="87b38-115">Dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="87b38-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="87b38-116">Aktarım Türü benzersiz olarak tanımlayan kullanıcı tanımlı bir anahtarı içerir.</span><span class="sxs-lookup"><span data-stu-id="87b38-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="87b38-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="87b38-117">transportConfigurationType</span></span>|<span data-ttu-id="87b38-118">Belirli aktarım uygulayan türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="87b38-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87b38-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87b38-119">Child Elements</span></span>  
 <span data-ttu-id="87b38-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="87b38-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87b38-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87b38-121">Parent Elements</span></span>  
  
|<span data-ttu-id="87b38-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="87b38-122">Element</span></span>|<span data-ttu-id="87b38-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87b38-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87b38-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="87b38-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="87b38-125">Belirli aktarım uygulama türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="87b38-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87b38-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="87b38-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87b38-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87b38-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="87b38-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="87b38-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
