---
title: '&lt;Meta verileri&gt;'
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 119cd4d5b63f8d957bc6db9dd6aabdf9e2beeb64
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147375"
---
# <a name="ltmetadatagt"></a><span data-ttu-id="9fa9d-102">&lt;Meta verileri&gt;</span><span class="sxs-lookup"><span data-stu-id="9fa9d-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="9fa9d-103">Hizmet meta verileri nasıl işleyebileceğiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="9fa9d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9fa9d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9fa9d-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="9fa9d-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa9d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fa9d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fa9d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fa9d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9fa9d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fa9d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9fa9d-109">Attributes</span></span>  
 <span data-ttu-id="9fa9d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9fa9d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fa9d-111">Child Elements</span></span>  
  
|<span data-ttu-id="9fa9d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9fa9d-112">Element</span></span>|<span data-ttu-id="9fa9d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fa9d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fa9d-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="9fa9d-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="9fa9d-115">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="9fa9d-116">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="9fa9d-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="9fa9d-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="9fa9d-118">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="9fa9d-119">Bir WSDL içeri Aktarıcı yanı sıra meta veri alma, bu sözleşmeyi temsil eden çeşitli sınıf bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="9fa9d-120">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="9fa9d-121">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9fa9d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9fa9d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9fa9d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9fa9d-123">Element</span></span>|<span data-ttu-id="9fa9d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fa9d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fa9d-125">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="9fa9d-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="9fa9d-126">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fa9d-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa9d-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="9fa9d-128">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9fa9d-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="9fa9d-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="9fa9d-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
