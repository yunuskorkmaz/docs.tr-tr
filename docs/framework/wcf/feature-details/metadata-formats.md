---
title: Meta Veri Biçimleri
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: e7208a8d5fd6d100ac2a2c4fb1369a571c63e7fc
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212179"
---
# <a name="metadata-formats"></a>Meta Veri Biçimleri
Windows Communication Foundation (WCF), aşağıdaki tablodaki meta veri biçimlerini destekler.  
  
## <a name="metadata-specifications-and-usage"></a>Meta veri belirtimleri ve kullanımı  
  
|Protokol|Belirtim ve kullanım|  
|--------------|-----------------------------|  
|WSDL 1,1|[Web Hizmetleri Açıklama Dili (WSDL) 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF, hizmetleri anlatmak için Web Hizmetleri Açıklama Dili (WSDL) kullanır.|  
|XML Şeması|[XML şeması Bölüm 2: veri türleri Ikinci sürüm](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) ve [XML şeması Bölüm 1: yapılar ikinci sürüm](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF, iletilerde kullanılan veri türlerini betimleyen XML şemasını kullanır.|  
|WS Ilkesi|[Web Hizmetleri Ilkesi 1,2-Framework (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Web Hizmetleri Ilkesi 1,5-Framework](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini tanımlamaya yönelik etki alanına özgü onaylarla WS-Policy 1,2 veya 1,5 belirtimlerini kullanır.|  
|WS Ilke ekleri|[Web Hizmetleri Ilkesi 1,2-ek (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF, WSDL 'deki çeşitli kapsamlara ilke ifadeleri eklemek için WS-Policy eklerini uygular.|  
|WS meta veri değişimi|[Web Hizmetleri meta veri değişimi (WS-MetadataExchange) sürüm 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
|WSDL için WS adresleme bağlaması|[Web Hizmetleri adresleme 1,0-WSDL bağlama](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF, WSDL 'ye adres bilgilerini eklemek için WS-Addressing bağlamasını uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL ve İlke](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
