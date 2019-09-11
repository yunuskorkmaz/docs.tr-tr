---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854762"
---
# <a name="wsdlimporter"></a><span data-ttu-id="34ae8-101">\<Wsdlıter ></span><span class="sxs-lookup"><span data-stu-id="34ae8-101">\<wsdlImporter></span></span>
<span data-ttu-id="34ae8-102">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ae8-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="34ae8-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34ae8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34ae8-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="34ae8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="34ae8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="34ae8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="34ae8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<meta veri >** ](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="34ae8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="34ae8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="34ae8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="34ae8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Wsdlıter >**</span><span class="sxs-lookup"><span data-stu-id="34ae8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34ae8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34ae8-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34ae8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ae8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="34ae8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34ae8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34ae8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34ae8-112">Attributes</span></span>  
  
|<span data-ttu-id="34ae8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="34ae8-113">Attribute</span></span>|<span data-ttu-id="34ae8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ae8-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="34ae8-115">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="34ae8-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34ae8-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ae8-116">Child Elements</span></span>  
 <span data-ttu-id="34ae8-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="34ae8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34ae8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34ae8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="34ae8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="34ae8-119">Element</span></span>|<span data-ttu-id="34ae8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34ae8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34ae8-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="34ae8-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="34ae8-122">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirtir.</span><span class="sxs-lookup"><span data-stu-id="34ae8-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34ae8-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34ae8-123">Remarks</span></span>  
 <span data-ttu-id="34ae8-124">Bir WSDL İçeri Aktarıcı, meta verileri içeri aktarmak ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34ae8-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="34ae8-125">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34ae8-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="34ae8-126">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="34ae8-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34ae8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34ae8-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="34ae8-128">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="34ae8-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="34ae8-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="34ae8-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
