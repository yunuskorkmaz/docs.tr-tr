---
title: Uygulama geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0f86b2569b9d4864586a0a7daea0ae5d3b901fd4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205271"
---
# <a name="pnrp-in-application-development"></a>Uygulama geliştirmede PNRP
Windows Vista'da adı yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimiyle (API) ağ uygulamalarına erişebilirsiniz.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü'nü uygulama  
 Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmedi; PNRP bileşeni, uygun bulut birleştirme ve bulutlarda yayımlamak için adresleri otomatik olarak belirler.  
  
 Son derece Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adları artık Windows Sockets işlevi getaddrinfo() tümleştirilmiştir. PNRP bir IPv6 adresi için bir ad çözümlemede kullanmak için uygulamaları getaddrinfo() işlevi tam olarak nitelikli etki alanı adı (FQDN) name.prnp.net çözümlemek için kullanabilir hangi çözümlenen Eş adı addır. Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.  
  
 İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](https://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer>
