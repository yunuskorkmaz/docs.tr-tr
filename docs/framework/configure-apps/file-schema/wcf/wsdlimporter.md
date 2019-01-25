---
title: '&lt;WsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 5f3d53111c4d303146701b03d7e7b32833cd9edd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651051"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="cca0d-102">&lt;WsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="cca0d-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="cca0d-103">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="cca0d-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="cca0d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cca0d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cca0d-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="cca0d-105">\<client></span></span>  
<span data-ttu-id="cca0d-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="cca0d-106">\<metadata></span></span>  
<span data-ttu-id="cca0d-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="cca0d-107">\<wsdlImporters></span></span>  
<span data-ttu-id="cca0d-108">\<WsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="cca0d-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca0d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cca0d-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cca0d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cca0d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cca0d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cca0d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cca0d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cca0d-112">Attributes</span></span>  
  
|<span data-ttu-id="cca0d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cca0d-113">Attribute</span></span>|<span data-ttu-id="cca0d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cca0d-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cca0d-115">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="cca0d-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cca0d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cca0d-116">Child Elements</span></span>  
 <span data-ttu-id="cca0d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="cca0d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cca0d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cca0d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cca0d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="cca0d-119">Element</span></span>|<span data-ttu-id="cca0d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cca0d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cca0d-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="cca0d-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="cca0d-122">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="cca0d-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cca0d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cca0d-123">Remarks</span></span>  
 <span data-ttu-id="cca0d-124">Bir WSDL içeri Aktarıcı yanı sıra meta veri alma, bu sözleşmeyi temsil eden çeşitli sınıf bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cca0d-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="cca0d-125">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cca0d-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="cca0d-126">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="cca0d-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca0d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cca0d-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="cca0d-128">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="cca0d-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="cca0d-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="cca0d-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
