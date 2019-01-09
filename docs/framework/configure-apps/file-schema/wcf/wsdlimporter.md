---
title: '&lt;WsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 43c1a50c740cd9c75ee641e4ac4d0fa8ea3ca36b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144996"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="7bcbb-102">&lt;WsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="7bcbb-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="7bcbb-103">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="7bcbb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7bcbb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bcbb-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="7bcbb-105">\<client></span></span>  
<span data-ttu-id="7bcbb-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="7bcbb-106">\<metadata></span></span>  
<span data-ttu-id="7bcbb-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="7bcbb-107">\<wsdlImporters></span></span>  
<span data-ttu-id="7bcbb-108">\<WsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="7bcbb-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bcbb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bcbb-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bcbb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bcbb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bcbb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bcbb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bcbb-112">Attributes</span></span>  
  
|<span data-ttu-id="7bcbb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bcbb-113">Attribute</span></span>|<span data-ttu-id="7bcbb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bcbb-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="7bcbb-115">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bcbb-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bcbb-116">Child Elements</span></span>  
 <span data-ttu-id="7bcbb-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bcbb-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bcbb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7bcbb-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bcbb-119">Element</span></span>|<span data-ttu-id="7bcbb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bcbb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bcbb-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="7bcbb-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="7bcbb-122">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bcbb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bcbb-123">Remarks</span></span>  
 <span data-ttu-id="7bcbb-124">Bir WSDL içeri Aktarıcı yanı sıra meta veri alma, bu sözleşmeyi temsil eden çeşitli sınıf bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="7bcbb-125">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="7bcbb-126">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bcbb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bcbb-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="7bcbb-128">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7bcbb-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="7bcbb-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="7bcbb-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
