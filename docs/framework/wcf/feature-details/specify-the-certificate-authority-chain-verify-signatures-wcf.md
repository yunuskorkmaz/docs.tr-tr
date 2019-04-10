---
title: 'Nasıl yapılır: (WCF) imzaları doğrulamak için kullanılan sertifika yetkilendirme sertifika zincirini belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 43296fad9519a08db5facdd220492ac70dffeca2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224488"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Nasıl yapılır: (WCF) imzaları doğrulamak için kullanılan sertifika yetkilendirme sertifika zincirini belirtme
Windows Communication Foundation (WCF) bir X.509 sertifikası ile imzalanmış bir SOAP ileti aldığında, varsayılan olarak, X.509 Sertifika bir güvenilen sertifika yetkilisi tarafından verildiğini doğrular. Bu sertifika deposunda aramak ve sertifikayı, sertifika yetkilisi olarak belirlendi güvenilen belirleme gerçekleştirilir. Bunun belirlenmesi WCF için sırada doğru sertifika deposunda sertifika yetkilendirme sertifika zincirini yüklenmesi gerekir.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Bir sertifika yetkilendirme sertifika zincirini yüklemek için  
  
-   SOAP ileti alıcısı güven amaçlayan her sertifika yetkilisi, verilen X.509 sertifikalarının yükleyin sertifika yetkilendirme sertifika zincirini sertifika deposuna WCF X.509 sertifikaları almak için yapılandırılır.  
  
     Örneğin, bir SOAP ileti alıcısı, Microsoft tarafından verilen X.509 sertifikalarının güven vermeyi planlıyorsa Microsoft Sertifika Yetkilendirme sertifika zincirini X.509 sertifikasından aramak için WCF ayarlayın sertifika deposunda yüklenmelidir. X.509 sertifikalarını WCF aradığı sertifika deposu, kod veya yapılandırma belirtilebilir. Örneğin, bu kodu kullanarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi veya yapılandırma dahil olmak üzere birkaç yolu [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Windows varsayılan sertifika zincirleri güvenilen sertifika yetkilileri için bir dizi ile birlikte gelen çünkü tüm sertifika yetkilileri sertifika zincirinin yüklemek için gerekli olmayabilir.  
  
    1.  Sertifika Yetkilendirme sertifika zincirini dışarı aktarın.  
  
         Tam olarak nasıl yapıldığını sertifika yetkilisinde bağlıdır. Sertifika yetkilisi Microsoft Sertifika Hizmetleri çalıştırıyorsa seçin **bir CA sertifikası, sertifika zinciri veya CRL indir**ve ardından **CA sertifikasını indir**.  
  
    2.  Sertifika Yetkilendirme sertifika zincirini içeri aktarın.  
  
         Microsoft Yönetim Konsolu (MMC)'da, Sertifikalar ek bileşenini açın. Sertifika deposu için WCF, arasından seçim X.509 sertifikaları almak için yapılandırılmış **güvenilen kök** **sertifika yetkilileri** klasör. Altında **güvenilen kök sertifika yetkilileri** klasörü sağ tıklatın **sertifikaları** klasörünü **tüm görevler**ve ardından **içeri aktarma** . Adımda dışarı aktardığınız dosya sağlayan bir.  
  
         Sertifikalar ek bileşenini MMC ile kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
