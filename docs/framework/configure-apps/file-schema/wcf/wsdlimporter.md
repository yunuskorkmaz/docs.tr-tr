---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915184"
---
# <a name="wsdlimporter"></a><span data-ttu-id="156bb-101">\<Wsdlıter ></span><span class="sxs-lookup"><span data-stu-id="156bb-101">\<wsdlImporter></span></span>
<span data-ttu-id="156bb-102">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="156bb-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="156bb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="156bb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="156bb-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="156bb-104">\<client></span></span>  
<span data-ttu-id="156bb-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="156bb-105">\<metadata></span></span>  
<span data-ttu-id="156bb-106">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="156bb-106">\<wsdlImporters></span></span>  
<span data-ttu-id="156bb-107">\<Wsdlıter ></span><span class="sxs-lookup"><span data-stu-id="156bb-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156bb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="156bb-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="156bb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="156bb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="156bb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="156bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="156bb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="156bb-111">Attributes</span></span>  
  
|<span data-ttu-id="156bb-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="156bb-112">Attribute</span></span>|<span data-ttu-id="156bb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156bb-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="156bb-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="156bb-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="156bb-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="156bb-115">Child Elements</span></span>  
 <span data-ttu-id="156bb-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="156bb-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="156bb-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="156bb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="156bb-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="156bb-118">Element</span></span>|<span data-ttu-id="156bb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="156bb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="156bb-120">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="156bb-120">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="156bb-121">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="156bb-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="156bb-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="156bb-122">Remarks</span></span>  
 <span data-ttu-id="156bb-123">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="156bb-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="156bb-124">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="156bb-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="156bb-125">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="156bb-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156bb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="156bb-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="156bb-127">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="156bb-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="156bb-128">İstemciler</span><span class="sxs-lookup"><span data-stu-id="156bb-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
