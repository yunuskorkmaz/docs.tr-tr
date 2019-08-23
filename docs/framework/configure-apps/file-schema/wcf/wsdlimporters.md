---
title: <wsdlImporters>
ms.date: 03/30/2017
ms.assetid: 270c7f93-eab7-47b6-8b94-ac3f5b7f17e4
ms.openlocfilehash: da9ab00c86e7f2657bfc28724d328ccbbc6957b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915161"
---
# <a name="wsdlimporters"></a><span data-ttu-id="37b1d-101">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="37b1d-101">\<wsdlImporters></span></span>
<span data-ttu-id="37b1d-102">Bu yapılandırma öğesi, WS-Policy ekleriyle Web Hizmetleri Açıklama Dili (WSDL) 1,1 meta verilerini içe aktaran tüm WSDL Importers 'ları belirler.</span><span class="sxs-lookup"><span data-stu-id="37b1d-102">This configuration element specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="37b1d-103">Her alt öğe, meta verileri`wsdlImporter`içeri aktarma yolunu belirten ve bu bilgileri sözleşme ve uç nokta bilgilerini temsil eden çeşitli sınıflara dönüştüren bir < >.</span><span class="sxs-lookup"><span data-stu-id="37b1d-103">Each child element is a <`wsdlImporter`> that specifies the way to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="37b1d-104">İçeri aktarma hatalarını ortaya çıkaran ve içeri aktarma ve dönüştürme işlemiyle ilgili tür bilgilerini kabul eden sözleşme ve uç nokta bilgilerini ve özelliklerini seçerek içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37b1d-104">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="37b1d-105">Ayrıca, herhangi bir ilke belgelerine, WSDL belgelerine, WSDL uzantılarına ve XML şema belgelerine erişim sağlayan bağlama bilgilerini ve özelliklerini içeri aktarmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="37b1d-105">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b1d-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37b1d-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="37b1d-107">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="37b1d-107">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="37b1d-108">İstemciler</span><span class="sxs-lookup"><span data-stu-id="37b1d-108">Clients</span></span>](../../../wcf/feature-details/clients.md)
