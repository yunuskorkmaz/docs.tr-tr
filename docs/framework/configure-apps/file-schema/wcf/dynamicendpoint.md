---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: e1a53869faa1997d2e79c3d2869a15001ee29626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673166"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="de1b6-101">\<dynamicEndpoint ></span><span class="sxs-lookup"><span data-stu-id="de1b6-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="de1b6-102">Bu yapılandırma öğesi, çalışma zamanında dinamik olarak uç nokta adresini bulabilirsiniz bir istemci programı olarak çalışması bir uygulamanın işlemesini etkinleştirmek için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de1b6-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="de1b6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de1b6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="de1b6-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="de1b6-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de1b6-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de1b6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de1b6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="de1b6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de1b6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de1b6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de1b6-108">Attributes</span></span>  
 <span data-ttu-id="de1b6-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="de1b6-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de1b6-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de1b6-110">Child Elements</span></span>  
  
|<span data-ttu-id="de1b6-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="de1b6-111">Element</span></span>|<span data-ttu-id="de1b6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de1b6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de1b6-113">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="de1b6-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="de1b6-114">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="de1b6-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de1b6-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de1b6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="de1b6-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="de1b6-116">Element</span></span>|<span data-ttu-id="de1b6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de1b6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de1b6-118">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="de1b6-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="de1b6-119">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="de1b6-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de1b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de1b6-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
