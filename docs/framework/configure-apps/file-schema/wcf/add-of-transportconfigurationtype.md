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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb00a5d5a2b4f64cdce6832faef4822b63f426d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="8bd9c-102">&lt;transportConfigurationType&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="8bd9c-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="8bd9c-103">Belirli bir türünü tanımlayan bir anahtar/değer çifti öğedir.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="8bd9c-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8bd9c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8bd9c-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="8bd9c-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="8bd9c-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="8bd9c-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="8bd9c-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="8bd9c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd9c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bd9c-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bd9c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bd9c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8bd9c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bd9c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8bd9c-111">Attributes</span></span>  
  
|<span data-ttu-id="8bd9c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8bd9c-112">Attribute</span></span>|<span data-ttu-id="8bd9c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bd9c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bd9c-114">name</span><span class="sxs-lookup"><span data-stu-id="8bd9c-114">name</span></span>|<span data-ttu-id="8bd9c-115">Dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="8bd9c-116">Aktarım Türü benzersiz olarak tanımlayan kullanıcı tanımlı bir anahtarı içerir.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="8bd9c-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="8bd9c-117">transportConfigurationType</span></span>|<span data-ttu-id="8bd9c-118">Belirli aktarım uygulayan türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bd9c-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bd9c-119">Child Elements</span></span>  
 <span data-ttu-id="8bd9c-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bd9c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8bd9c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8bd9c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8bd9c-122">Element</span></span>|<span data-ttu-id="8bd9c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bd9c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bd9c-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="8bd9c-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="8bd9c-125">Belirli aktarım uygulama türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8bd9c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd9c-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8bd9c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd9c-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="8bd9c-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="8bd9c-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
