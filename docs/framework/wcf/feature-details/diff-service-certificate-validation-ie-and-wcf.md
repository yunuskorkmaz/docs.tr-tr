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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
Internet Explorer ve Windows Communication Foundation (WCF) 'nin HTTPS kullanıldığında hizmet sertifikalarını doğrulama yöntemi arasındaki fark nedeniyle, bir WCF istemcisi hizmet uç noktalarına başarıyla ileti gönderebilse de, Internet Explorer 'ın yardım sayfasına veya bir hizmetin Web Hizmetleri Açıklama diline (WSDL) erişemez olması mümkündür. Bunun nedeni, Internet Explorer 'ın `ServerAuthentication` Gelişmiş kullanım bayraklarında hizmet sertifikasının nesne tanımlayıcıları (OID) olup olmadığını denetlemesi, ancak WCF böyle bir kısıtlamayı zorunlu kılmaz. Internet Explorer hizmet yardım sayfasına veya hizmet için WSDL 'ye erişe, hizmet meta verilerine erişmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
