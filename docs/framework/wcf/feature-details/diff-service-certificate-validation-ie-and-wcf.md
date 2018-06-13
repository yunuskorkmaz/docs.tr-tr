---
title: Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: ecc2b16eae5428e305f5f6096d6d7994256d86c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488692"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
HTTPS kullanıldığında, Internet Explorer'ı ve Windows Communication Foundation (WCF) hizmetini sertifikaları doğrulamak yolu arasındaki fark nedeniyle, Internet Explorer Yardım sayfası veya Web Hizmetleri Açıklama Dili erişmek mümkün olmaz mümkündür (WSDL) bir WCF İstemcisi başarıyla yapabileceksiniz olsa bile bir hizmeti için hizmet uç noktalarına iletileri göndermek. Internet Explorer denetler bu hizmet sertifikası olup çünkü `ServerAuthentication` WCF böyle bir sınırlama uygulamaz ancak Gelişmiş kullanımı bayrakları nesne tanımlayıcıları (OID). Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
