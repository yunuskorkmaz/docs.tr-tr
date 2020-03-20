---
title: 'Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184903"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme
X.509 sertifikasını Windows Communication Foundation (WCF) tarafından erişilebilir hale getirmek için uygulama kodunun sertifika deposu adını ve konumunu belirtmesi gerekir. Bazı durumlarda, işlem kimliğinin X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyaya erişimi olmalıdır. Bir sertifika deposunda X.509 sertifikasıyla ilişkili özel anahtarı elde etmek için WCF'nin bunu yapmak için izni olması gerekir. Varsayılan olarak, sertifikanın özel anahtarına yalnızca sahibi ve Sistem hesabı erişebilir.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X.509 sertifikalarını WCF için erişilebilir hale getirmek için  
  
1. WCF'nin çalıştırdığı hesaba X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyaya okuma erişimi verin.  
  
    1. WCF'nin X.509 sertifikası için özel anahtara okuma erişimi gerekip gerekmediğini belirleyin.  
  
         Aşağıdaki tabloda, X.509 sertifikası kullanırken özel bir anahtarın kullanılabilir olup olmadığı açıklanacaktır.  
  
        |X.509 sertifika kullanımı|Özel anahtar|  
        |---------------------------|-----------------|  
        |Giden SOAP mesajını dijital olarak imzalıyorum.|Evet|  
        |Gelen SOAP iletisinin imzasını doğrulama.|Hayır|  
        |Giden SOAP iletisi şifreleme.|Hayır|  
        |Gelen SOAP iletisini çözme.|Evet|  
  
    2. Sertifika deposunun konumunu ve adını belirleyin.  
  
         Sertifikanın depolandığı sertifika deposu, uygulama kodunda veya yapılandırmada belirtilir. Örneğin, aşağıdaki örnekte sertifikanın adlı `CurrentUser` `My`sertifika deposunda bulunduğu belirtilir.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Sertifikanın özel anahtarının [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracını kullanarak bilgisayarda nerede bulunduğunu belirleyin.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika deposunun adını, sertifika deposunun konumunu ve sertifikayı benzersiz olarak tanımlayan bir şey gerektirir. Araç, sertifikanın özne adını veya parmak izini benzersiz bir tanımlayıcı olarak kabul eder. Sertifikanın parmak izini nasıl belirleyiniz hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
  
         Aşağıdaki kod örneği, `My` mağazadaki `CurrentUser` bir sertifikanın özel anahtarının konumunu belirlemek için [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`aracını kullanır.  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. WCF'nin altında çalışan hesabı belirleyin.  
  
         Aşağıdaki tablo, WCF'nin belirli bir senaryo için çalıştırdığı hesabı ayrıntılarıyla açıklar.  
  
        |Senaryo|İşlem kimliği|  
        |--------------|----------------------|  
        |İstemci (konsol veya WinForms uygulaması).|Şu anda kullanıcı oturum açtı.|  
        |Kendi kendine barındırılan hizmet.|Şu anda kullanıcı oturum açtı.|  
        |IIS 6.0 (Windows Server 2003) veya IIS 7.0 'de (Windows Vista) barındırılan hizmet.|AĞ HİzMETİ|  
        |IIS 5.X'te (Windows XP) barındırılan hizmet.|Machine.config dosyasındaki `<processModel>` öğe tarafından kontrol edilir. Varsayılan hesap ASPNET'tir.|  
  
    5. Icacls.exe gibi bir aracı kullanarak WCF'nin altında çalıştırdığı hesabın özel anahtarını içeren dosyaya okuma erişimi ver.  
  
         Aşağıdaki kod örneği, belirtilen dosyanın NETWORK SERVICE hesabına okuma (:R) dosyaya erişim hakkı vermesi için isteğe bağlı erişim kontrol listesini (DACL) yönetmelikle tir.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
