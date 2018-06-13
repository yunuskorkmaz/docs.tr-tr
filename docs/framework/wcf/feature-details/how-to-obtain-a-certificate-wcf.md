---
title: 'Nası yapılır: Sertifika Edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 368401d91aa2a83110631d583660d6ccebf8d4fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491513"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Nası yapılır: Sertifika Edinme (WCF)
Windows Communication Foundation (WCF) kullanmak için X.509 sertifikaları, özelliklerini kullanmak, yalnızca ilk sertifika edinin.  
  
### <a name="to-obtain-an-x509-certificate"></a>Bir X.509 sertifikası almak için  
  
1.  Aşağıdakilerden birini seçin:  
  
    -   VeriSign, Inc. gibi bir sertifika yetkilisinden bir sertifika satın alın  
  
    -   Kendi sertifika hizmetini kurma ve sertifika imzalama sertifika yetkilisine sahip. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server destekleyen ortak anahtar altyapısı (PKI) Sertifika Hizmetleri içerir. Windows Server 2008'de kullanmak [Active Directory Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkID=153483) bir sertifika yetkilisi yönetmek için rol.  
  
    -   Kendi sertifika hizmetini kurma ve yapın sahip Sertifika imzalı değil.  
  
    > [!NOTE]
    >  Uygulamanız, yaklaşımı X.509 sertifikasını içeren SOAP isteği alıcısı X.509 sertifikası güvenmesi gerekir. Bunun anlamı X.509 sertifika veya sertifika zincirinde bir veren güvenilir kişiler sertifika deposunda olduğunu ve X.509 sertifikası Güvenilmeyen Sertifikalar deposunda değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
