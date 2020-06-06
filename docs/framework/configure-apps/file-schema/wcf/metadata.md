---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855231"
---
# \<metadata>
<span data-ttu-id="34fb7-101">Hizmet meta verilerinin nasıl işlenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="34fb7-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="34fb7-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34fb7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34fb7-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34fb7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="34fb7-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34fb7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34fb7-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34fb7-105">Attributes</span></span>  
 <span data-ttu-id="34fb7-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="34fb7-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34fb7-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34fb7-107">Child Elements</span></span>  
  
|<span data-ttu-id="34fb7-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="34fb7-108">Element</span></span>|<span data-ttu-id="34fb7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34fb7-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="34fb7-110">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34fb7-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="34fb7-111">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34fb7-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="34fb7-112">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe alan tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="34fb7-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="34fb7-113">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34fb7-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="34fb7-114">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34fb7-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="34fb7-115">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="34fb7-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34fb7-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34fb7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="34fb7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="34fb7-117">Element</span></span>|<span data-ttu-id="34fb7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34fb7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="34fb7-119">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34fb7-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34fb7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34fb7-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="34fb7-121">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="34fb7-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="34fb7-122">İstemciler</span><span class="sxs-lookup"><span data-stu-id="34fb7-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
