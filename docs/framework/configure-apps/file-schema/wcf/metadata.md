---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: c0c9848d073c799e1f97dd79b375848dfab71e99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763912"
---
# <a name="metadata"></a><span data-ttu-id="5d936-101">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="5d936-101">\<metadata></span></span>
<span data-ttu-id="5d936-102">Hizmet meta verileri nasıl işleyebileceğiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d936-102">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="5d936-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5d936-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5d936-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="5d936-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d936-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d936-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d936-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d936-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5d936-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d936-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d936-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d936-108">Attributes</span></span>  
 <span data-ttu-id="5d936-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d936-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d936-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d936-110">Child Elements</span></span>  
  
|<span data-ttu-id="5d936-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d936-111">Element</span></span>|<span data-ttu-id="5d936-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d936-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d936-113">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="5d936-113">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="5d936-114">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d936-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="5d936-115">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d936-115">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="5d936-116">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="5d936-116">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="5d936-117">WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d936-117">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="5d936-118">Bir WSDL içeri Aktarıcı yanı sıra meta veri alma, bu sözleşmeyi temsil eden çeşitli sınıf bilgilerini ve uç nokta bilgileri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d936-118">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="5d936-119">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d936-119">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="5d936-120">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="5d936-120">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d936-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d936-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5d936-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d936-122">Element</span></span>|<span data-ttu-id="5d936-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d936-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d936-124">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="5d936-124">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="5d936-125">İstemci bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d936-125">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d936-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d936-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="5d936-127">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="5d936-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="5d936-128">İstemciler</span><span class="sxs-lookup"><span data-stu-id="5d936-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
