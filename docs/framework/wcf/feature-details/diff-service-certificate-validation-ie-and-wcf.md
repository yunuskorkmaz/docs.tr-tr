---
description: 'Hakkında daha fazla bilgi: Internet Explorer ve WCF tarafından yapılan hizmet sertifikası doğrulaması arasındaki farklılıklar'
title: Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 2d635aec0949ec4e65cd965089206bbf6d6815a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756363"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="5571b-103">Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5571b-103">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>

<span data-ttu-id="5571b-104">Internet Explorer ve Windows Communication Foundation (WCF) 'nin HTTPS kullanıldığında hizmet sertifikalarını doğrulama yöntemi arasındaki fark nedeniyle, bir WCF istemcisi hizmet uç noktalarına başarıyla ileti gönderebilse de, Internet Explorer 'ın yardım sayfasına veya bir hizmetin Web Hizmetleri Açıklama diline (WSDL) erişemez olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5571b-104">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="5571b-105">Bunun nedeni, Internet Explorer 'ın `ServerAuthentication` Gelişmiş kullanım bayraklarında hizmet sertifikasının nesne tanımlayıcıları (OID) olup olmadığını denetlemesi, ancak WCF böyle bir kısıtlamayı zorunlu kılmaz.</span><span class="sxs-lookup"><span data-stu-id="5571b-105">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="5571b-106">Internet Explorer hizmet yardım sayfasına veya hizmet için WSDL 'ye erişe, hizmet meta verilerine erişmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5571b-106">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5571b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5571b-107">See also</span></span>

- [<span data-ttu-id="5571b-108">HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları</span><span class="sxs-lookup"><span data-stu-id="5571b-108">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="5571b-109">Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="5571b-109">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
