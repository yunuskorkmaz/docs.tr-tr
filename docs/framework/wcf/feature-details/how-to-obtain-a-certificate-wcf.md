---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sertifika edinme (WCF)'
title: 'Nası yapılır: Sertifika Edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 2ca40c9646bbdeb6c29a94966fd24ec00d9b5306
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793707"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Nası yapılır: Sertifika Edinme (WCF)

X. 509.440 sertifikalarını kullanan Windows Communication Foundation (WCF) özelliklerinden herhangi birini kullanmak için öncelikle sertifikaları edinmeniz yeterlidir.  
  
### <a name="to-obtain-an-x509-certificate"></a>X. 509.440 sertifikası almak için  
  
1. Aşağıdakilerden birini seçin:  
  
    - VeriSign, Inc. bir sertifika yetkilisinden sertifika satın alın.  
  
    - Kendi sertifika hizmetinizi kurun ve sertifikaları imzalamak için bir sertifika yetkilisine sahip olmanız gerekir. Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server hepsi ortak anahtar altyapısını (PKI) destekleyen sertifika hizmetlerini içerir. Windows Server 2008 ' de, sertifika yetkilisini yönetmek için [Active Directory Sertifika Hizmetleri](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) rolünü kullanın.  
  
    - Kendi sertifika hizmetinizi kurun ve sertifikalara kaydolmayın.  
  
    > [!NOTE]
    > Hangi yaklaşımı kullanırsanız, X. 509.440 sertifikasını içeren SOAP isteğinin alıcısı X. 509.440 sertifikasına güvenmelidir. Yani, sertifika zincirindeki X. 509.440 sertifikası veya veren, güvenilen kişiler sertifika deposunda ve X. 509.440 sertifikasının Güvenilmeyen sertifikalar deposunda olmadığı anlamına gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
- [Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma](how-to-create-temporary-certificates-for-use-during-development.md)
