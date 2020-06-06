---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854762"
---
# \<wsdlImporter>
<span data-ttu-id="fb06c-101">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb06c-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="fb06c-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb06c-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb06c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb06c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fb06c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb06c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb06c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb06c-105">Attributes</span></span>  
  
|<span data-ttu-id="fb06c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb06c-106">Attribute</span></span>|<span data-ttu-id="fb06c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb06c-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="fb06c-108">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="fb06c-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb06c-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb06c-109">Child Elements</span></span>  
 <span data-ttu-id="fb06c-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb06c-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb06c-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb06c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="fb06c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb06c-112">Element</span></span>|<span data-ttu-id="fb06c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb06c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="fb06c-114">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb06c-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb06c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb06c-115">Remarks</span></span>  
 <span data-ttu-id="fb06c-116">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fb06c-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="fb06c-117">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb06c-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="fb06c-118">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="fb06c-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb06c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb06c-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="fb06c-120">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="fb06c-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="fb06c-121">İstemciler</span><span class="sxs-lookup"><span data-stu-id="fb06c-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
