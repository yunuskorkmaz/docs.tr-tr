---
title: PNRP uygulama geliştirme
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pnrp-in-application-development"></a>PNRP uygulama geliştirme
Windows Vista'da ağ uygulamaları ad yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimi (API) erişebilir.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü'nü uygulama  
 Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmeyen; PNRP bileşen otomatik olarak uygun bulut birleştirme ve Bulutlar içinde yayımlamak için adresleri belirler.  
  
 Yüksek oranda Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adlarını artık Windows yuvaları işlevi getaddrinfo() tümleşiktir. Bir IPv6 adresi için bir adı çözümlemek için PNRP kullanmak için uygulamaları getaddrinfo() işlevi tam etki alanı adı (FQDN) name.prnp.net çözmek için kullanabilir hangi adının çözümlendiği eş adıdır. Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.  
  
 İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](http://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.PeerToPeer>
