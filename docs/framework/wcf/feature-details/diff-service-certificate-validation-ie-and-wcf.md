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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar

Internet Explorer ve Windows Communication Foundation (WCF) 'nin HTTPS kullanıldığında hizmet sertifikalarını doğrulama yöntemi arasındaki fark nedeniyle, bir WCF istemcisi hizmet uç noktalarına başarıyla ileti gönderebilse de, Internet Explorer 'ın yardım sayfasına veya bir hizmetin Web Hizmetleri Açıklama diline (WSDL) erişemez olması mümkündür. Bunun nedeni, Internet Explorer 'ın `ServerAuthentication` Gelişmiş kullanım bayraklarında hizmet sertifikasının nesne tanımlayıcıları (OID) olup olmadığını denetlemesi, ancak WCF böyle bir kısıtlamayı zorunlu kılmaz. Internet Explorer hizmet yardım sayfasına veya hizmet için WSDL 'ye erişe, hizmet meta verilerine erişmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
