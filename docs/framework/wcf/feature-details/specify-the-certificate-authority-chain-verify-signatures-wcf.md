---
title: "Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ea15e8fe9580f561eedf048ed2aaf2e2ed248f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)
Zaman [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] varsayılan doğrular X.509 sertifikası güvenilen bir sertifika yetkilisi tarafından verilmiş bir X.509 sertifikası ile imzalanmış bir SOAP iletisi alır. Bu sertifika deposunda bakarak ve sertifika, sertifika yetkilisi olarak belirlendiyse için güvenilir belirleme gerçekleştirilir. Sırayla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bunun belirlenmesi için sertifika yetkilendirme sertifika zincirini doğru sertifika depolama alanına yüklenmelidir.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Bir sertifika yetkilendirme sertifika zincirini yüklemek için  
  
-   SOAP ileti alıcısı X.509 sertifikaları veren güven amaçlayan her sertifika yetkilisi için yükleme sertifikanın sertifika yetkilisi sertifikası zincirine depolamak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikaları almak için yapılandırılmış Kaynak.  
  
     Örneğin, bir SOAP iletisi alıcı Microsoft tarafından verilen X.509 sertifikalarının güvenmeyi çalışırsa, sertifika yetkilendirme sertifika zincirini Microsoft Sertifika yüklenmelidir için depolanacak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikalarını aramak için ayarlama Kaynak. Sertifika deposunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikalarını kod veya yapılandırma belirtilen için arar. Örneğin, bu kodu kullanarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi ya da dahil olmak üzere birkaç şekilde yapılandırmasında [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Varsayılan Sertifika zincirleri güvenilen sertifika yetkilileri için bir dizi Windows birlikte olduğundan, tüm sertifika yetkilileri sertifika zinciri yüklemek gerekli olmayabilir.  
  
    1.  Sertifika Yetkilendirme sertifika zincirini verin.  
  
         Tam olarak bunun nasıl yapılacağı sertifika yetkilisinde bağlıdır. Sertifika yetkilisi Microsoft Sertifika Hizmetleri çalıştırılıyorsa seçin **bir CA sertifikası, sertifika zinciri veya CRL indir**ve ardından **CA sertifikasını indir**.  
  
    2.  Sertifika Yetkilendirme sertifika zincirini içeri aktarın.  
  
         Microsoft Yönetim Konsolu (MMC)'da, Sertifikalar ek bileşenini açın. Sertifika için depolama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seçin, X.509 sertifikaları almak için yapılandırılmış **güvenilen kök** **sertifika yetkilileri**klasör. Altında **güvenilen kök sertifika yetkilileri** klasörünü sağ tıklatın **sertifikaları**klasörünü **tüm görevler**ve ardından **alma** . Adımda dışarı dosyası sağlamanız bir.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Sertifikalar ek bileşenini MMC ile bkz [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
