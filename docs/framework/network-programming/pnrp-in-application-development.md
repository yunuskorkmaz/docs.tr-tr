---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428212"
---
# <a name="pnrp-in-application-development"></a>Uygulama Geliştirmede PNRP
Windows Vista 'da, ağ uygulamaları basitleştirilmiş bir PNRP uygulama programlama arabirimi (API) aracılığıyla ad yayınına ve çözüm işlevlerine erişebilirler.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş adı çözümleme protokolünü uygulama  
 Basitleştirilmiş PNRP API 'SI ile, bulutlar adı ve adresleri kaydetmek için açıkça belirtilmez; PNRP bileşeni, katılacak uygun bulutları ve bulutlar içinde yayımlanacak adresleri otomatik olarak belirler.  
  
 Windows Vista 'da yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için, PNRP adları artık GetAddrInfo () Windows Yuvaları işleviyle tümleşiktir. Bir adı bir IPv6 adresine çözümlemek üzere PNRP kullanmak için, uygulamalar, ad eş adı olan tam etki alanı adı (FQDN) name.prnp.net çözümlemek için GetAddrInfo () işlevini kullanabilir. Pnrp.net etki alanı, Windows Vista 'da PNRP ad çözümlemesi için ayrılmış bir etki alanıdır.  
  
 PeerToPeer uygulamaları arasında geçen ileti, hala PeerChannel ve WCF [büyük veri ve akış](../wcf/feature-details/large-data-and-streaming.md)gibi temel mimarilerde işlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
