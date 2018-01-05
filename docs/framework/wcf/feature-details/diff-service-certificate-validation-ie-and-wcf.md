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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Internet Explorer ve WCF Tarafından Yapılan Sertifika Doğrulama Arasındaki Farklar
Internet Explorer yolu arasındaki fark nedeniyle ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet sertifikaları doğrulamak HTTPS kullanıldığında, Internet Explorer Yardım sayfası veya bir hizmetin Web Hizmetleri Açıklama Dili (WSDL) bile erişmek mümkün olmaz mümkündür Ancak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci başarıyla hizmet uç noktaları için iletileri gönderebilir. Internet Explorer denetler bu hizmet sertifikası olup çünkü `ServerAuthentication` ancak nesne tanımlayıcıları (OID), Gelişmiş kullanımı bayrakları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] böyle bir sınırlama uygulamaz. Internet Explorer hizmeti Yardım sayfası veya hizmet için WSDL erişemiyor kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti meta verilere erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
