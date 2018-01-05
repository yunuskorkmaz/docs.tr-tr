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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12e30d9df9d6bb0a9f8776099951e4354d302ebf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="39fdd-102">Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="39fdd-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="39fdd-103">Internet Explorer yolu arasındaki fark nedeniyle ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sertifikaları doğrulamak HTTPS kullanıldığında, Internet Explorer Yardım sayfası veya bir hizmetin Web Hizmetleri Açıklama Dili (WSDL) bile erişmek mümkün olmaz mümkündür Ancak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci başarıyla hizmet uç noktaları için iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="39fdd-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="39fdd-104">Internet Explorer denetler bu hizmet sertifikası olup çünkü `ServerAuthentication` ancak nesne tanımlayıcıları (OID), Gelişmiş kullanımı bayrakları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] böyle bir sınırlama uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="39fdd-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="39fdd-105">Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="39fdd-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39fdd-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39fdd-106">See Also</span></span>  
 [<span data-ttu-id="39fdd-107">HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları</span><span class="sxs-lookup"><span data-stu-id="39fdd-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="39fdd-108">Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="39fdd-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
