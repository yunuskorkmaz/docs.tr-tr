---
title: Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857707"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="54e8d-102">Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="54e8d-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="54e8d-103">HTTPS kullanıldığında, Internet Explorer ve Windows Communication Foundation (WCF) hizmet sertifikalarını doğrulamak şekilde arasında farklılık nedeniyle, Internet Explorer Web Hizmetleri Açıklama Dili ve yardım sayfasına erişmek mümkün olmayacaktır mümkündür (WSDL) bir WCF İstemcisi başarıyla için mümkün olsa da bir hizmeti için hizmet uç noktalarını ileti gönderme.</span><span class="sxs-lookup"><span data-stu-id="54e8d-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="54e8d-104">Internet Explorer denetler. Bu hizmet sertifikası olup çünkü `ServerAuthentication` WCF böyle bir sınırlama uygulamaz ancak Gelişmiş kullanımı bayrakları nesne tanımlayıcıları (OID).</span><span class="sxs-lookup"><span data-stu-id="54e8d-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="54e8d-105">Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="54e8d-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e8d-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e8d-106">See also</span></span>

- [<span data-ttu-id="54e8d-107">HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları</span><span class="sxs-lookup"><span data-stu-id="54e8d-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="54e8d-108">Nasıl yapılır: Meta veri alma ve uyumlu bir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="54e8d-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
