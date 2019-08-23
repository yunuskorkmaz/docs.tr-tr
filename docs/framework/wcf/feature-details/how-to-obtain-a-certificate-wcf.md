---
title: 'Nasıl yapılır: Sertifika edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929185"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Nasıl yapılır: Sertifika edinme (WCF)
X. 509.440 sertifikalarını kullanan Windows Communication Foundation (WCF) özelliklerinden herhangi birini kullanmak için öncelikle sertifikaları edinmeniz yeterlidir.  
  
### <a name="to-obtain-an-x509-certificate"></a>X. 509.440 sertifikası almak için  
  
1. Aşağıdakilerden birini seçin:  
  
    - VeriSign, Inc. bir sertifika yetkilisinden sertifika satın alın.  
  
    - Kendi sertifika hizmetinizi kurun ve sertifikaları imzalamak için bir sertifika yetkilisine sahip olmanız gerekir. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server hepsi ortak anahtar altyapısını (PKI) destekleyen sertifika hizmetlerini içerir. Windows Server 2008 ' de, sertifika yetkilisini yönetmek için [Active Directory Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=153483) rolünü kullanın.  
  
    - Kendi sertifika hizmetinizi kurun ve sertifikalara kaydolmayın.  
  
    > [!NOTE]
    > Hangi yaklaşımı kullanırsanız, X. 509.440 sertifikasını içeren SOAP isteğinin alıcısı X. 509.440 sertifikasına güvenmelidir. Yani, sertifika zincirindeki X. 509.440 sertifikası veya veren, güvenilen kişiler sertifika deposunda ve X. 509.440 sertifikasının Güvenilmeyen sertifikalar deposunda olmadığı anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nasıl yapılır: Geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
