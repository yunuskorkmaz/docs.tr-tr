---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 4555dc9c2e0b783de2fb57e47c9aada0d69462e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931313"
---
# <a name="metadata"></a><span data-ttu-id="c0176-101">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="c0176-101">\<metadata></span></span>
<span data-ttu-id="c0176-102">Hizmet meta verilerinin nasıl işlenemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0176-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="c0176-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0176-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0176-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="c0176-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0176-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0176-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0176-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0176-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c0176-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0176-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0176-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0176-108">Attributes</span></span>  
 <span data-ttu-id="c0176-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c0176-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0176-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0176-110">Child Elements</span></span>  
  
|<span data-ttu-id="c0176-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0176-111">Element</span></span>|<span data-ttu-id="c0176-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0176-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0176-113">\<PolicyImporters ></span><span class="sxs-lookup"><span data-stu-id="c0176-113">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="c0176-114">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0176-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="c0176-115">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0176-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="c0176-116">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="c0176-116">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="c0176-117">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe alan tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0176-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="c0176-118">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0176-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="c0176-119">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0176-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="c0176-120">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="c0176-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0176-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0176-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c0176-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0176-122">Element</span></span>|<span data-ttu-id="c0176-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0176-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0176-124">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="c0176-124">\<client></span></span>](client.md)|<span data-ttu-id="c0176-125">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0176-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0176-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0176-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="c0176-127">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c0176-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c0176-128">İstemciler</span><span class="sxs-lookup"><span data-stu-id="c0176-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
