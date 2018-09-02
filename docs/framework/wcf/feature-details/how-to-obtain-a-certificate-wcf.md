---
title: 'Nası yapılır: Sertifika Edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465868"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Nası yapılır: Sertifika Edinme (WCF)
Windows Communication Foundation (WCF) kullanmak için yalnızca ilk sertifikaları almak, X.509 sertifikaları, özelliklerini kullanın.  
  
### <a name="to-obtain-an-x509-certificate"></a>Bir X.509 sertifikası almak için  
  
1.  Aşağıdakilerden birini seçin:  
  
    -   VeriSign gibi bir sertifika yetkilisinden bir sertifika satın alın  
  
    -   Kendi sertifika hizmetini ayarlama ve bir sertifika yetkilisi sertifikaları imzalamak sahip. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 veri merkezi sunucusu destekleyen ortak anahtar altyapısı (PKI) Sertifika Hizmetleri içerir. Windows Server 2008'de kullanmak [Active Directory Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=153483) bir sertifika yetkilisi yönetmek için rol.  
  
    -   Kendi sertifika hizmetini ayarlama ve yapmak sahip sertifikaları imzalı değil.  
  
    > [!NOTE]
    >  Yaklaşımı, uygulamanız, alıcı X.509 sertifikasını içeren SOAP isteğinin X.509 sertifikası güvenmesi gerekir. Başka bir deyişle, X.509 sertifika veya sertifika zincirinde bir veren güvenilir kişiler sertifika deposunda olduğunu ve X.509 sertifika güvenilmeyen bir sertifika deposunda değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
