---
title: WCF'de Güvenlik Değerlendirmeleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601042"
---
# <a name="security-considerations-in-wcf"></a>WCF'de Güvenlik Değerlendirmeleri
Bu bölümdeki konularda, Windows Communication Foundation (WCF) uygulaması tasarlarken göz önünde bulundurmanız gereken güvenlikle ilgili çeşitli öğeler listelenir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bilgileri Açıklama](information-disclosure.md)  
 Bilgilerin açıklanmasında veya saldırıya neden olabilecek çeşitli yollar ve bunun nasıl azaltılacağını ele alınmaktadır.  
  
 [Ayrıcalıkların Yükseltilmesi](elevation-of-privilege.md)  
 Başlangıçta verilen ve bu sorunu hafifletmenin ötesinde bir saldırgan yetkilendirme izinleri verme etkilerini açıklar.  
  
 [Hizmet Reddi](denial-of-service.md)  
 Bir sistem iletileri uygun şekilde işleyemezse ne olduğunu ve bunun nasıl azaltılacağını açıklar.  
  
 [İzinsiz Değişiklik](tampering.md)  
 İletilerin değiştirilmesini veya iletilerin teslimini ve bunun nasıl azaltılacağını ele alır.  
  
 [Yeniden Yürütme Saldırıları](replay-attacks.md)  
 Bir saldırgan bir ileti akışını iki taraf arasında kopyaladığında ne olduğunu ve akışın bir veya daha fazla tarafın akışını yeniden oynadığını ve bunun nasıl azaltılacağını açıklar.  
  
 [Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar](security-considerations-for-secure-sessions.md)  
 Güvenli oturumları uygularken güvenliği etkileyen aşağıdaki öğeleri açıklar.  
  
 [Desteklenmeyen Senaryolar](unsupported-scenarios.md)  
 Belirli güvenlik yönlerini desteklemeyen çeşitli senaryolar listeler ve kaçınılması veya dikkate alınmamalıdır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Güvenlik Kılavuzu ve En İyi Uygulamalar](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security.md)
