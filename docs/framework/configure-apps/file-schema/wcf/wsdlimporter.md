---
title: '&lt;WsdlImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc85c93dc73918d661195e33ce5094622db36af4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="3d91a-102">&lt;WsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="3d91a-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="3d91a-103">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d91a-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="3d91a-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3d91a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d91a-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="3d91a-105">\<client></span></span>  
<span data-ttu-id="3d91a-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="3d91a-106">\<metadata></span></span>  
<span data-ttu-id="3d91a-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="3d91a-107">\<wsdlImporters></span></span>  
<span data-ttu-id="3d91a-108">\<WsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="3d91a-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d91a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d91a-109">Syntax</span></span>  
  
```xml  
<metadata>  
  <wsdlImporters>  
    <wsdlImporter type="string" />  
  </wsdlImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d91a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d91a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d91a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3d91a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d91a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3d91a-112">Attributes</span></span>  
  
|<span data-ttu-id="3d91a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3d91a-113">Attribute</span></span>|<span data-ttu-id="3d91a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d91a-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3d91a-115">Bu öğe türü.</span><span class="sxs-lookup"><span data-stu-id="3d91a-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d91a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d91a-116">Child Elements</span></span>  
 <span data-ttu-id="3d91a-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="3d91a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d91a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3d91a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3d91a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3d91a-119">Element</span></span>|<span data-ttu-id="3d91a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d91a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d91a-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="3d91a-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="3d91a-122">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d91a-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d91a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d91a-123">Remarks</span></span>  
 <span data-ttu-id="3d91a-124">WSDL alma yanı sıra meta veri içe bu sözleşmeyi temsil eden çeşitli sınıflar bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3d91a-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="3d91a-125">Sözleşme ve uç nokta bilgileri ve kullanıma alma hataları ve tür bilgilerini içeri aktarma ve dönüştürme işlemi için ilgili kabul özellikleri seçerek aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d91a-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="3d91a-126">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgelerinde erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="3d91a-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d91a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d91a-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="3d91a-128">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="3d91a-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="3d91a-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="3d91a-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
