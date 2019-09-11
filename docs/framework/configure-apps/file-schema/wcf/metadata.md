---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855231"
---
# <a name="metadata"></a><span data-ttu-id="29a00-101">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="29a00-101">\<metadata></span></span>
<span data-ttu-id="29a00-102">Hizmet meta verilerinin nasıl işlenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29a00-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="29a00-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29a00-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29a00-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29a00-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29a00-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="29a00-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="29a00-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<meta veri >**</span><span class="sxs-lookup"><span data-stu-id="29a00-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a00-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29a00-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29a00-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a00-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29a00-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29a00-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29a00-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29a00-110">Attributes</span></span>  
 <span data-ttu-id="29a00-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="29a00-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29a00-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a00-112">Child Elements</span></span>  
  
|<span data-ttu-id="29a00-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="29a00-113">Element</span></span>|<span data-ttu-id="29a00-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a00-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29a00-115">\<PolicyImporters ></span><span class="sxs-lookup"><span data-stu-id="29a00-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="29a00-116">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29a00-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="29a00-117">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29a00-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="29a00-118">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="29a00-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="29a00-119">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe alan tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="29a00-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="29a00-120">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="29a00-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="29a00-121">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29a00-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="29a00-122">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="29a00-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29a00-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29a00-123">Parent Elements</span></span>  
  
|<span data-ttu-id="29a00-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="29a00-124">Element</span></span>|<span data-ttu-id="29a00-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29a00-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29a00-126">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="29a00-126">\<client></span></span>](client.md)|<span data-ttu-id="29a00-127">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29a00-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29a00-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29a00-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="29a00-129">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="29a00-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="29a00-130">İstemciler</span><span class="sxs-lookup"><span data-stu-id="29a00-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
