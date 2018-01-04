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
ms.workload: dotnet
ms.openlocfilehash: 2b52345ae30ab56a6f34d2aa46f9836d67555b15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-lttransportconfigurationtypegt"></a><span data-ttu-id="40c26-102">&lt;transportConfigurationType&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="40c26-102">&lt;add&gt; of &lt;transportConfigurationType&gt;</span></span>
<span data-ttu-id="40c26-103">Belirli bir türünü tanımlayan bir anahtar/değer çifti öğedir.</span><span class="sxs-lookup"><span data-stu-id="40c26-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
 <span data-ttu-id="40c26-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40c26-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40c26-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="40c26-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="40c26-106">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="40c26-106">\<transportConfigurationTypes></span></span>  
<span data-ttu-id="40c26-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="40c26-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c26-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40c26-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40c26-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c26-109">Attributes and Elements</span></span>  
 <span data-ttu-id="40c26-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40c26-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40c26-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40c26-111">Attributes</span></span>  
  
|<span data-ttu-id="40c26-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="40c26-112">Attribute</span></span>|<span data-ttu-id="40c26-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40c26-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="40c26-114">name</span><span class="sxs-lookup"><span data-stu-id="40c26-114">name</span></span>|<span data-ttu-id="40c26-115">Dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="40c26-115">Required String attribute.</span></span><br /><br /> <span data-ttu-id="40c26-116">Aktarım Türü benzersiz olarak tanımlayan kullanıcı tanımlı bir anahtarı içerir.</span><span class="sxs-lookup"><span data-stu-id="40c26-116">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="40c26-117">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="40c26-117">transportConfigurationType</span></span>|<span data-ttu-id="40c26-118">Belirli aktarım uygulayan türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="40c26-118">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40c26-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c26-119">Child Elements</span></span>  
 <span data-ttu-id="40c26-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="40c26-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40c26-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c26-121">Parent Elements</span></span>  
  
|<span data-ttu-id="40c26-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="40c26-122">Element</span></span>|<span data-ttu-id="40c26-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40c26-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40c26-124">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="40c26-124">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="40c26-125">Belirli aktarım uygulama türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="40c26-125">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="40c26-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="40c26-126">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40c26-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40c26-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="40c26-128">Barındırma</span><span class="sxs-lookup"><span data-stu-id="40c26-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
