---
title: "Nası yapılır: Sertifika Edinme (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Nası yapılır: Sertifika Edinme (WCF)
Herhangi birini kullanmak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , özelliklerini kullanmak X.509 sertifikalarını, yalnızca ilk sertifikaları edinin.  
  
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
