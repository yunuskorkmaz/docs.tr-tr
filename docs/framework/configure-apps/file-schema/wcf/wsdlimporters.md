---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: 81fb25f6a77456608fd3cb0d5e73f67c7f7867c3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274579"
---
# <a name="wsdlimporters"></a><span data-ttu-id="71140-101">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="71140-101">\<wsdlImporters></span></span>
<span data-ttu-id="71140-102">Bu yapılandırma öğesi, WS-Policy ekli Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran tüm WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="71140-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="71140-103">Her alt öğesi olan bir <`wsdlImporter`> yanı sıra meta verileri içeri aktarmak için bu bilgileri, sözleşmeyi ve uç nokta bilgilerini temsil eden çeşitli sınıflara Dönüştür biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="71140-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="71140-104">Sözleşmeyi ve uç nokta bilgilerini ve kullanıma alma hataları ve içeri aktarma ve dönüştürme işlemi için uygun tür bilgilerini kabul özellikleri seçerek alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71140-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="71140-105">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgeleri için erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="71140-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71140-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71140-106">See also</span></span>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="71140-107">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="71140-107">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="71140-108">İstemciler</span><span class="sxs-lookup"><span data-stu-id="71140-108">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
