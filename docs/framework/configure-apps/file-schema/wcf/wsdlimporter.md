---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 1f34486296465b3ea0b5b05bd9492062c85ad8c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670254"
---
# <a name="wsdlimporter"></a><span data-ttu-id="519c7-101">\<WsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="519c7-101">\<wsdlImporter></span></span>
<span data-ttu-id="519c7-102">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="519c7-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="519c7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="519c7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="519c7-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="519c7-104">\<client></span></span>  
<span data-ttu-id="519c7-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="519c7-105">\<metadata></span></span>  
<span data-ttu-id="519c7-106">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="519c7-106">\<wsdlImporters></span></span>  
<span data-ttu-id="519c7-107">\<WsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="519c7-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519c7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="519c7-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="519c7-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="519c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="519c7-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="519c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="519c7-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="519c7-111">Attributes</span></span>  
  
|<span data-ttu-id="519c7-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="519c7-112">Attribute</span></span>|<span data-ttu-id="519c7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="519c7-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="519c7-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="519c7-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="519c7-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="519c7-115">Child Elements</span></span>  
 <span data-ttu-id="519c7-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="519c7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="519c7-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="519c7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="519c7-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="519c7-118">Element</span></span>|<span data-ttu-id="519c7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="519c7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="519c7-120">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="519c7-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="519c7-121">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="519c7-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="519c7-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="519c7-122">Remarks</span></span>  
 <span data-ttu-id="519c7-123">Bir WSDL içeri Aktarıcı yanı sıra meta veri alma, bu sözleşmeyi temsil eden çeşitli sınıf bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="519c7-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="519c7-124">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="519c7-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="519c7-125">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="519c7-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519c7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="519c7-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="519c7-127">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="519c7-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="519c7-128">İstemciler</span><span class="sxs-lookup"><span data-stu-id="519c7-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
