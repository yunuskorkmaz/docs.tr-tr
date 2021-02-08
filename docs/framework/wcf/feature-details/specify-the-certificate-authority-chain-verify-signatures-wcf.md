---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Imzaları doğrulamak için kullanılan sertifika yetkilisi sertifika zincirini belirtme (WCF)'
title: 'Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: f3bfcb378641db2a4bdba054f25042a5e7e9be07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793460"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)

Windows Communication Foundation (WCF) bir X. 509.952 sertifikası kullanılarak imzalanmış bir SOAP iletisi aldığında, varsayılan olarak X. 509.440 sertifikasının güvenilen bir sertifika yetkilisi tarafından verildiğini doğrular. Bu, bir sertifika deposuna bakarak ve bu sertifika yetkilisinin sertifikasının güvenilir olarak belirlenmiş olup olmadığı belirlenerek yapılır. WCF 'nin bu belirleme yapması için, sertifika yetkilisi sertifika zincirinin doğru sertifika deposuna yüklenmesi gerekir.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Sertifika yetkilisi sertifika zinciri yüklemek için  
  
- Bir SOAP ileti alıcısının, ' den çıkarılan X. 509.952 sertifikalarına güvenmesini amaçlayan her bir sertifika yetkilisi için, sertifika yetkilisi sertifika zincirini WCF 'nin from X. 509.952 sertifikalarını almak üzere yapılandırıldığı sertifika deposuna yükler.  
  
     Örneğin, bir SOAP ileti alıcısı Microsoft tarafından verilen X. 509.440 sertifikalarına güvenmeyi amaçladığında, Microsoft için sertifika yetkilisi sertifika zinciri, WCF 'nin ' den X. 509.952 sertifikalarını aramak üzere ayarlandığı sertifika deposunda yüklü olmalıdır. WCF 'nin X için aradığı sertifika depolama alanı, kod veya yapılandırmada bir. 509.440 sertifikası belirtilebilir. Örneğin, bu kod, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi kullanılarak veya yapılandırma içinde, dahil olmak üzere birkaç yolla belirtilebilir [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Windows, güvenilen sertifika yetkilileri için bir dizi varsayılan sertifika zinciriyle birlikte geldiği için, sertifika zincirini tüm sertifika yetkilileri için yüklemek gerekli olmayabilir.  
  
    1. Sertifika yetkilisi sertifika zincirini dışarı aktarın.  
  
         Bu işlem, sertifika yetkilisine göre tam olarak nasıl yapılır? Sertifika yetkilisi Microsoft Sertifika Hizmetleri çalıştırıyorsa, **CA sertifikası, sertifika zinciri veya CRL indir**' i seçin ve ardından **CA sertifikasını indir**' i seçin.  
  
    2. Sertifika yetkilisi sertifika zincirini içeri aktarın.  
  
         Microsoft Yönetim Konsolu 'nda (MMC), Sertifikalar ek bileşenini açın. WCF 'nin içinden X. 509.952 sertifikalarını almak üzere yapılandırıldığı sertifika deposunda, **Güvenilen kök** **sertifika yetkilileri** klasörünü seçin. **Güvenilen kök sertifika yetkilileri** klasörü altında, **Sertifikalar** klasörüne sağ tıklayın, **Tüm görevler**' ın üzerine gelin ve ardından **içeri aktar**' a tıklayın. A adımında dosyaya aktarılmış dosyayı sağlayın.  
  
         MMC ile Sertifikalar ek bileşenini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
