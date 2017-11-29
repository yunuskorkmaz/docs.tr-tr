---
title: "Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d4dee17b60d83f6019eda3f6431813911d3468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme
Bir X.509 sertifikası erişilebilir olmasını sağlamak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], uygulama kodu sertifika deposu adını ve konumunu belirtmelisiniz. Bazı durumlarda, işlem kimliği, X.509 sertifikayla ilişkili özel anahtarı içeren dosyayı için erişimi olması gerekir. Bir sertifika deposunda bir X.509 sertifikası ile ilişkili özel anahtarı edinme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bunu yapmak için izni olmalıdır. Varsayılan olarak, yalnızca sahibi ve sistem hesabı, bir sertifikanın özel anahtarı erişebilir.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X.509 sertifikalarını WCF için erişilebilir hale getirmek için  
  
1.  Hesap vermek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikayla ilişkili özel anahtarı içeren dosya için okuma erişimi çalıştırıyor.  
  
    1.  Belirlemek olup olmadığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 Sertifika özel anahtarına okuma erişimi gerektirir.  
  
         Bir özel anahtar bir X.509 sertifikası kullanırken kullanılabilir olmalıdır yoksa aşağıdaki tabloda ayrıntılı olarak açıklanmaktadır.  
  
        |X.509 sertifika kullan|Özel anahtar|  
        |---------------------------|-----------------|  
        |Giden SOAP ileti dijital olarak imzalamak.|Evet|  
        |Gelen bir SOAP iletisi imzası doğrulanıyor.|Hayır|  
        |Giden SOAP ileti şifreleme.|Hayır|  
        |Gelen bir SOAP iletisi çözme.|Evet|  
  
    2.  Sertifikanın depolandığı adı ve sertifika deposu konumunu belirler.  
  
         Sertifikanın depolandığı sertifika deposu uygulama kodu veya yapılandırmasında belirtilir. Örneğin, aşağıdaki örnek sertifika bulunan belirtir `CurrentUser` adlı sertifika deposuna `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Kullanarak, sertifikanın özel anahtarı bilgisayarda bulunduğu belirlemek [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika depolama alanı adı, sertifika deposu konumu ve sertifika benzersiz olarak tanımlayan bir şey gerektirir. Aracı sertifikanın konu adı veya kendi parmak izi benzersiz bir tanımlayıcı olarak kabul eder. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir sertifika parmak izini belirlemek için bkz: nasıl [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Aşağıdaki kod örneğinde [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) sertifikada özel anahtarı konumunu belirlemek için aracı `My` depolamak `CurrentUser` parmak izi ile `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Hesabı belirleyin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altında çalışıyor.  
  
         Aşağıdaki tabloda hesabıyla ayrıntıları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] belirli bir senaryo için çalışıyor.  
  
        |Senaryo|İşlem kimliği|  
        |--------------|----------------------|  
        |İstemci (konsol veya WinForms uygulama).|Şu anda oturum açmış kullanıcı.|  
        |Kendini barındıran hizmet.|Şu anda oturum açmış kullanıcı.|  
        |IIS 6. 0'barındırılan hizmeti ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|AĞ HİZMETİ|  
        |Hizmet barındırılan IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Tarafından denetlenen `<processModel>` Machine.config dosyasındaki öğesi. ASPNET varsayılan hesaptır.|  
  
    5.  Hesap için özel anahtarı içeren dosyayı okuma erişimi verme, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cacls.exe gibi bir araç kullanarak çalışan altında.  
  
         Aşağıdaki kod örneği düzenlemeleri (/ E) vermek belirtilen dosya için erişim denetim listesi (ACL) (/ G) ağ hizmeti hesabının okuma (: R) dosyaya erişimi.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Sertifikalar ile çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
