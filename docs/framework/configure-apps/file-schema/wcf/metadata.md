---
title: '&lt;Meta veriler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 147af2a40994b7889551d1a3f521e8c097610050
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmetadatagt"></a><span data-ttu-id="80fd8-102">&lt;Meta veriler&gt;</span><span class="sxs-lookup"><span data-stu-id="80fd8-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="80fd8-103">Hizmet meta verilerini nasıl işlenebilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fd8-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="80fd8-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="80fd8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80fd8-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="80fd8-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fd8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80fd8-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80fd8-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80fd8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="80fd8-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80fd8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80fd8-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80fd8-109">Attributes</span></span>  
 <span data-ttu-id="80fd8-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="80fd8-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80fd8-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80fd8-111">Child Elements</span></span>  
  
|<span data-ttu-id="80fd8-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="80fd8-112">Element</span></span>|<span data-ttu-id="80fd8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80fd8-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80fd8-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="80fd8-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="80fd8-115">Özel ilke onaylamalarını bağlamaları hakkında alma Denetim İlkesi ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fd8-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="80fd8-116">İlke içeri Aktarıcı yanı sıra özellikleri bağlama hakkında özel ilke onaylamalarını arama onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80fd8-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="80fd8-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="80fd8-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="80fd8-118">WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta veri içe tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="80fd8-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="80fd8-119">WSDL alma yanı sıra meta veri içe bu sözleşmeyi temsil eden çeşitli sınıflar bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80fd8-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="80fd8-120">Sözleşme ve uç nokta bilgileri ve kullanıma alma hataları ve tür bilgilerini içeri aktarma ve dönüştürme işlemi için ilgili kabul özellikleri seçerek aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80fd8-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="80fd8-121">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgelerinde erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="80fd8-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80fd8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80fd8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="80fd8-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="80fd8-123">Element</span></span>|<span data-ttu-id="80fd8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80fd8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80fd8-125">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="80fd8-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="80fd8-126">İstemci, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80fd8-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80fd8-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80fd8-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="80fd8-128">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="80fd8-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="80fd8-129">İstemciler</span><span class="sxs-lookup"><span data-stu-id="80fd8-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
