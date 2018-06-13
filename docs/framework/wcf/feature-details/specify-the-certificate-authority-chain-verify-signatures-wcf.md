---
title: 'Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 14f7691046f9512e25006bd6cd02749eed825003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498081"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)
Windows Communication Foundation (WCF) bir X.509 sertifikası ile imzalanmış bir SOAP iletisi aldığında, varsayılan olarak, X.509 sertifikası güvenilen bir sertifika yetkilisi tarafından verilmiş olduğunu doğrular. Bu sertifika deposunda bakarak ve sertifika, sertifika yetkilisi olarak belirlendiyse için güvenilir belirleme gerçekleştirilir. Bunun belirlenmesi WCF için sırayla sertifika yetkilendirme sertifika zincirini doğru sertifika deposuna yüklenmesi gerekir.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Bir sertifika yetkilendirme sertifika zincirini yüklemek için  
  
-   Bir SOAP iletisi alıcı güven amaçlayan her sertifika yetkilisi için verilen X.509 sertifikalarının yükleyin sertifika yetkilendirme sertifika zincirini sertifika deposuna WCF X.509 sertifikaları almak için yapılandırılır.  
  
     Örneği için bir SOAP iletisi alıcı Microsoft tarafından verilen X.509 sertifikalarının güvenmeyi çalışırsa, Microsoft Sertifika Yetkilendirme sertifika zincirini X.509 sertifikaları aramak için WCF ayarlamak sertifika deposuna yüklenmelidir. WCF X.509 sertifikalarını arar sertifika deposu, kod veya yapılandırma belirtilebilir. Örneğin, bu kodu kullanarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi ya da dahil olmak üzere birkaç şekilde yapılandırmasında [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Varsayılan Sertifika zincirleri güvenilen sertifika yetkilileri için bir dizi Windows birlikte olduğundan, tüm sertifika yetkilileri sertifika zinciri yüklemek gerekli olmayabilir.  
  
    1.  Sertifika Yetkilendirme sertifika zincirini verin.  
  
         Tam olarak bunun nasıl yapılacağı sertifika yetkilisinde bağlıdır. Sertifika yetkilisi Microsoft Sertifika Hizmetleri çalıştırılıyorsa seçin **bir CA sertifikası, sertifika zinciri veya CRL indir**ve ardından **CA sertifikasını indir**.  
  
    2.  Sertifika Yetkilendirme sertifika zincirini içeri aktarın.  
  
         Microsoft Yönetim Konsolu (MMC)'da, Sertifikalar ek bileşenini açın. İçin sertifika deposu seçin, X.509 sertifikaları almak için bu WCF yapılandırılmış **güvenilen kök** **sertifika yetkilileri**klasör. Altında **güvenilen kök sertifika yetkilileri** klasörünü sağ tıklatın **sertifikaları**klasörünü **tüm görevler**ve ardından **alma** . Adımda dışarı dosyası sağlamanız bir.  
  
         Sertifikalar ek bileşenini MMC ile kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
