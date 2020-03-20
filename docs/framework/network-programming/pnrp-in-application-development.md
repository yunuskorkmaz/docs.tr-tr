---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428212"
---
# <a name="pnrp-in-application-development"></a>Uygulama Geliştirmede PNRP
Windows Vista'da ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayını ve çözüm işlevlerine erişebilir.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolünün Uygulanması  
 Basitleştirilmiş PNRP API ile bulutlar, adı ve adresleri kaydetmek için açıkça belirtilmemiştir; PNRP bileşeni, katılmak için uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.  
  
 Windows Vista'da son derece basitleştirilmiş PNRP ad çözümü için, PNRP adları artık getaddrinfo() Windows Soketleri işlevine entegre edilmiştir. Bir adı IPv6 adresine çözmek için PNRP'yi kullanmak için, uygulamalar tam nitelikli alan adı (FQDN) name.prnp.net çözmek için getaddrinfo() işlevini kullanabilir ve bu ad eş adı çözümleniyor. pnrp.net etki alanı, PNRP ad çözümü için Windows Vista'da ayrılmış bir etki alanıdır.  
  
 PeerToPeer uygulamaları arasında geçen ileti hala PeerChannel ve WCF [Büyük Veri ve Akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarileri tarafından işlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
