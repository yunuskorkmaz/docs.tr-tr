---
title: '&lt;DynamicEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 78ec2d4639161f8e10105f205576f052c8a5567c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146842"
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="b8042-102">&lt;DynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="b8042-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="b8042-103">Bu yapılandırma öğesi, çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8042-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="b8042-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8042-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8042-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b8042-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8042-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8042-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8042-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8042-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8042-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8042-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8042-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8042-109">Attributes</span></span>  
 <span data-ttu-id="b8042-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8042-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8042-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8042-111">Child Elements</span></span>  
  
|<span data-ttu-id="b8042-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8042-112">Element</span></span>|<span data-ttu-id="b8042-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8042-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8042-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="b8042-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="b8042-115">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="b8042-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8042-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8042-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b8042-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8042-117">Element</span></span>|<span data-ttu-id="b8042-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8042-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8042-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="b8042-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="b8042-120">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="b8042-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8042-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8042-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
