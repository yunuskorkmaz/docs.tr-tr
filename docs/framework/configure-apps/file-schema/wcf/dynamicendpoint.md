---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: e1a53869faa1997d2e79c3d2869a15001ee29626
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187752"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="326ca-101">\<dynamicEndpoint ></span><span class="sxs-lookup"><span data-stu-id="326ca-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="326ca-102">Bu yapılandırma öğesi, çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="326ca-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="326ca-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="326ca-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="326ca-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="326ca-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="326ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="326ca-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="326ca-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="326ca-106">Attributes and Elements</span></span>  
 <span data-ttu-id="326ca-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="326ca-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="326ca-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="326ca-108">Attributes</span></span>  
 <span data-ttu-id="326ca-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="326ca-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="326ca-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="326ca-110">Child Elements</span></span>  
  
|<span data-ttu-id="326ca-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="326ca-111">Element</span></span>|<span data-ttu-id="326ca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="326ca-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="326ca-113">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="326ca-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="326ca-114">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="326ca-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="326ca-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="326ca-115">Parent Elements</span></span>  
  
|<span data-ttu-id="326ca-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="326ca-116">Element</span></span>|<span data-ttu-id="326ca-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="326ca-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="326ca-118">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="326ca-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="326ca-119">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="326ca-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="326ca-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="326ca-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
