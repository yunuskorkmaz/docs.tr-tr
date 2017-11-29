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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
Internet Explorer yolu arasındaki fark nedeniyle ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sertifikaları doğrulamak HTTPS kullanıldığında, Internet Explorer Yardım sayfası veya bir hizmetin Web Hizmetleri Açıklama Dili (WSDL) bile erişmek mümkün olmaz mümkündür Ancak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci başarıyla hizmet uç noktaları için iletileri gönderebilir. Internet Explorer denetler bu hizmet sertifikası olup çünkü `ServerAuthentication` ancak nesne tanımlayıcıları (OID), Gelişmiş kullanımı bayrakları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] böyle bir sınırlama uygulamaz. Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTPS, SSL TCP üzerinden sslve SOAP Güvenliği arasındaki sertifika doğrulama farkları](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Nasıl yapılır: meta verileri alma ve uyumlu bir hizmet ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
