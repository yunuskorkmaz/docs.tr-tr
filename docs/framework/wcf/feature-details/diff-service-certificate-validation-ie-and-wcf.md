---
title: Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 151075f2894b895ab90418748df9face3aa70252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599197"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="05b28-102">Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="05b28-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="05b28-103">Internet Explorer ve Windows Communication Foundation (WCF) 'nin HTTPS kullanıldığında hizmet sertifikalarını doğrulama yöntemi arasındaki fark nedeniyle, bir WCF istemcisi hizmet uç noktalarına başarıyla ileti gönderebilse de, Internet Explorer 'ın yardım sayfasına veya bir hizmetin Web Hizmetleri Açıklama diline (WSDL) erişemez olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="05b28-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="05b28-104">Bunun nedeni, Internet Explorer 'ın `ServerAuthentication` Gelişmiş kullanım bayraklarında hizmet sertifikasının nesne tanımlayıcıları (OID) olup olmadığını denetlemesi, ancak WCF böyle bir kısıtlamayı zorunlu kılmaz.</span><span class="sxs-lookup"><span data-stu-id="05b28-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="05b28-105">Internet Explorer hizmet yardım sayfasına veya hizmet için WSDL 'ye erişe, hizmet meta verilerine erişmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="05b28-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b28-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05b28-106">See also</span></span>

- [<span data-ttu-id="05b28-107">HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları</span><span class="sxs-lookup"><span data-stu-id="05b28-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="05b28-108">Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="05b28-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
