---
description: 'Hakkında daha fazla bilgi edinin: <wsdlImporter>'
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 9f95d4e6b940f36e9142eb9865327c772e3ce4db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682156"
---
# \<wsdlImporter>

<span data-ttu-id="489fe-102">Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini WS-Policy eklerle içe aktaran tüm WSDL Importers lerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="489fe-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="489fe-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="489fe-103">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="489fe-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="489fe-104">Attributes and Elements</span></span>  

 <span data-ttu-id="489fe-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="489fe-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="489fe-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="489fe-106">Attributes</span></span>  
  
|<span data-ttu-id="489fe-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="489fe-107">Attribute</span></span>|<span data-ttu-id="489fe-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="489fe-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="489fe-109">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="489fe-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="489fe-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="489fe-110">Child Elements</span></span>  

 <span data-ttu-id="489fe-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="489fe-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="489fe-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="489fe-112">Parent Elements</span></span>  
  
|<span data-ttu-id="489fe-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="489fe-113">Element</span></span>|<span data-ttu-id="489fe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="489fe-114">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="489fe-115">Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini WS-Policy eklerle içe aktaran tüm WSDL Importers lerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="489fe-115">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="489fe-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="489fe-116">Remarks</span></span>  

 <span data-ttu-id="489fe-117">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="489fe-117">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="489fe-118">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="489fe-118">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="489fe-119">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="489fe-119">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489fe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="489fe-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="489fe-121">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="489fe-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="489fe-122">İstemciler</span><span class="sxs-lookup"><span data-stu-id="489fe-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
