---
title: '&lt;wsdlImporters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c791ac53afa868bed2daee11eb787ed27efb731f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwsdlimportersgt"></a><span data-ttu-id="8e217-102">&lt;wsdlImporters&gt;</span><span class="sxs-lookup"><span data-stu-id="8e217-102">&lt;wsdlImporters&gt;</span></span>
<span data-ttu-id="8e217-103">Bu yapılandırma öğesi WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1.1 meta verileri içe aktaran WSDL ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e217-103">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="8e217-104">Her alt öğesi olan bir <`wsdlImporter`> yanı sıra meta verilerini içe aktarmak için bu bilgileri, sözleşmeyi ve uç nokta bilgileri temsil eden çeşitli sınıflara Dönüştür biçimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e217-104">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="8e217-105">Sözleşme ve uç nokta bilgileri ve kullanıma alma hataları ve tür bilgilerini içeri aktarma ve dönüştürme işlemi için ilgili kabul özellikleri seçerek aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e217-105">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="8e217-106">İçeri aktarma bağlama bilgileri ve ilke belgeleri, WSDL belgeleri, WSDL uzantıları ve XML Şeması belgelerinde erişim sağlayan özellikleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="8e217-106">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e217-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e217-107">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="8e217-108">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8e217-108">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="8e217-109">İstemciler</span><span class="sxs-lookup"><span data-stu-id="8e217-109">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
