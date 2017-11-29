---
title: "Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a58ea9f84571ede9943769e1f187a242383a88f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="cdf02-102">Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="cdf02-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="cdf02-103">Internet Explorer yolu arasındaki fark nedeniyle ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sertifikaları doğrulamak HTTPS kullanıldığında, Internet Explorer Yardım sayfası veya bir hizmetin Web Hizmetleri Açıklama Dili (WSDL) bile erişmek mümkün olmaz mümkündür Ancak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci başarıyla hizmet uç noktaları için iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="cdf02-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="cdf02-104">Internet Explorer denetler bu hizmet sertifikası olup çünkü `ServerAuthentication` ancak nesne tanımlayıcıları (OID), Gelişmiş kullanımı bayrakları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] böyle bir sınırlama uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="cdf02-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="cdf02-105">Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="cdf02-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf02-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdf02-106">See Also</span></span>  
 [<span data-ttu-id="cdf02-107">HTTPS, SSL TCP üzerinden sslve SOAP Güvenliği arasındaki sertifika doğrulama farkları</span><span class="sxs-lookup"><span data-stu-id="cdf02-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="cdf02-108">Nasıl yapılır: meta verileri alma ve uyumlu bir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="cdf02-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
