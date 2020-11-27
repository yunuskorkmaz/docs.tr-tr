---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 7c59b2be8384c8f8cc6bbdc4546a678cfe1c538d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263197"
---
# <a name="pnrp-in-application-development"></a>Uygulama Geliştirmede PNRP

Windows Vista 'da, ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayınına ve çözüm işlevlerine erişebilirler.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş adı çözümleme protokolünü uygulama  

 Basitleştirilmiş PNRP API 'SI ile, bulutlar adı ve adresleri kaydetmek için açıkça belirtilmez; PNRP bileşeni, katılacak uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.  
  
 Windows Vista 'da yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için, PNRP adları artık GetAddrInfo () Windows Yuvaları işleviyle tümleşiktir. Bir adı bir IPv6 adresine çözümlemek üzere PNRP kullanmak için, uygulamalar, ad eş adı olan tam etki alanı adı (FQDN) name.prnp.net çözümlemek için GetAddrInfo () işlevini kullanabilir. Pnrp.net etki alanı, Windows Vista 'da PNRP ad çözümlemesi için ayrılmış bir etki alanıdır.  
  
 PeerToPeer uygulamaları arasında geçen ileti, hala PeerChannel ve WCF [büyük veri ve akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarilerde işlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
