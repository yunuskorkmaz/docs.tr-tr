---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 4cd0d739e58cd252213e8d5c16d29cc612338df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980505"
---
# <a name="pnrp-in-application-development"></a>Uygulama Geliştirmede PNRP
Windows Vista'da adı yayını ve çözümleme işlevleri bir Basitleştirilmiş PNRP uygulama programlama arabirimiyle (API) ağ uygulamalarına erişebilirsiniz.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Eş Adı Çözümleme Protokolü'nü uygulama  
 Basitleştirilmiş PNRP API ile bulut açıkça adı ve adreslerini kaydetmek için belirtilmedi; PNRP bileşeni, uygun bulut birleştirme ve bulutlarda yayımlamak için adresleri otomatik olarak belirler.  
  
 Son derece Basitleştirilmiş PNRP ad çözümlemesi için Windows Vista'da, PNRP adları artık Windows Sockets işlevi getaddrinfo() tümleştirilmiştir. PNRP bir IPv6 adresi için bir ad çözümlemede kullanmak için uygulamaları getaddrinfo() işlevi tam olarak nitelikli etki alanı adı (FQDN) name.prnp.net çözümlemek için kullanabilir hangi çözümlenen Eş adı addır. Windows Vista'da ayrılmış olarak etki alanı PNRP ad çözümlemesi için pnrp.net etki alanıdır.  
  
 İleti PeerToPeer uygulamalar arasında geçirme PeerChannel'a ve WCF gibi temel mimarileri tarafından işlenen hala [büyük veriler ve akış](https://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.PeerToPeer>
