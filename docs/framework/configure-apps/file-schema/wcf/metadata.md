---
description: 'Hakkında daha fazla bilgi edinin: <metadata>'
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 6cc1e472dbada72fe6a375a6832e7c9128dcda6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684431"
---
# \<metadata>

<span data-ttu-id="da5e9-102">Hizmet meta verilerinin nasıl işlenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="da5e9-102">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="da5e9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="da5e9-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da5e9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="da5e9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="da5e9-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="da5e9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da5e9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="da5e9-106">Attributes</span></span>  

 <span data-ttu-id="da5e9-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="da5e9-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da5e9-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="da5e9-108">Child Elements</span></span>  
  
|<span data-ttu-id="da5e9-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="da5e9-109">Element</span></span>|<span data-ttu-id="da5e9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da5e9-110">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="da5e9-111">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da5e9-111">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="da5e9-112">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da5e9-112">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="da5e9-113">Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini WS-Policy eki ile içe alan WSDL Importers 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="da5e9-113">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="da5e9-114">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da5e9-114">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="da5e9-115">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da5e9-115">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="da5e9-116">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="da5e9-116">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da5e9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="da5e9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="da5e9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="da5e9-118">Element</span></span>|<span data-ttu-id="da5e9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da5e9-119">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="da5e9-120">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da5e9-120">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da5e9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da5e9-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="da5e9-122">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="da5e9-122">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="da5e9-123">İstemciler</span><span class="sxs-lookup"><span data-stu-id="da5e9-123">Clients</span></span>](../../../wcf/feature-details/clients.md)
