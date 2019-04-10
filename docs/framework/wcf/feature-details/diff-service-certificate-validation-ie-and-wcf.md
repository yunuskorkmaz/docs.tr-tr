---
title: Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225930"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
HTTPS kullanıldığında, Internet Explorer ve Windows Communication Foundation (WCF) hizmet sertifikalarını doğrulamak şekilde arasında farklılık nedeniyle, Internet Explorer Web Hizmetleri Açıklama Dili ve yardım sayfasına erişmek mümkün olmayacaktır mümkündür (WSDL) bir WCF İstemcisi başarıyla için mümkün olsa da bir hizmeti için hizmet uç noktalarını ileti gönderme. Internet Explorer denetler. Bu hizmet sertifikası olup çünkü `ServerAuthentication` WCF böyle bir sınırlama uygulamaz ancak Gelişmiş kullanımı bayrakları nesne tanımlayıcıları (OID). Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
