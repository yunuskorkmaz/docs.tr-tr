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
ms.openlocfilehash: 0917569b556c31413b715d75c83a96f3a4b015d7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579978"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme
X.509 sertifikası Windows Communication Foundation (WCF) için erişilebilir hale getirmek için uygulama kodu, sertifika deposu adını ve konumunu belirtmelisiniz. Bazı durumlarda, işlem kimliği X.509 sertifikası ile ilişkili özel anahtarı içeren dosyayı erişimi olmalıdır. Bir sertifika deposunda X.509 sertifikası ile ilişkili özel anahtarı almak için WCF, bunu yapmak için izni olmalıdır. Varsayılan olarak, bir sertifikanın özel anahtarı yalnızca sahibi ve System hesabıyla erişebilirsiniz.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X.509 sertifikalarını WCF için erişilebilir hale getirmek için  
  
1.  X.509 sertifikasıyla ilişkili özel anahtarı içeren dosyayı için okuma erişimi hangi WCF altında çalıştığı hesabın verin.  
  
    1.  WCF için X.509 sertifikası özel anahtarı için okuma erişimi gerekli olup olmadığını belirler.  
  
         Aşağıdaki tabloda, özel anahtarı kullanarak bir X.509 sertifikası olduğunda kullanılabilir olmalıdır yoksa ayrıntıları.  
  
        |X.509 sertifika kullan|özel anahtar|  
        |---------------------------|-----------------|  
        |Giden SOAP ileti imzalamak.|Evet|  
        |Gelen bir SOAP ileti imzası doğrulama.|Hayır|  
        |Giden SOAP ileti şifreleme.|Hayır|  
        |Gelen bir SOAP iletisi şifre çözme.|Evet|  
  
    2.  Sertifikanın depolandığı adı ve sertifika depo konumunu belirleyin.  
  
         Sertifika deposuna sertifikanın depolandığı, uygulama kodu veya yapılandırmada belirtilir. Örneğin, aşağıdaki örnekte sertifika bulunan belirtir `CurrentUser` adlı sertifika deposuna `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Kullanarak, sertifika özel anahtarını bilgisayarda nerede belirlemek [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) aracı, sertifika deposunun adını, sertifika depo konumunu ve sertifika benzersiz olarak tanımlayan bir şey gerektirir. Aracı sertifikanın konu adı veya parmak izi benzersiz bir tanımlayıcı olarak kabul eder. Bir sertifika parmak izini belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Aşağıdaki kod örneğinde [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) için sertifikada özel anahtar konumunu belirlemek için aracı `My` depolar `CurrentUser` parmak izi ile `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  WCF altında çalıştığı hesabı belirleyin.  
  
         Aşağıdaki tabloda, WCF, belirli bir senaryo için çalıştığı hesabı ayrıntıları.  
  
        |Senaryo|İşlem kimliği|  
        |--------------|----------------------|  
        |İstemci (konsol veya aplikace WinForms).|Şu anda oturum açmış kullanıcı.|  
        |Şirket içinde barındırılan hizmeti.|Şu anda oturum açmış kullanıcı.|  
        |IIS 6. 0'barındırılan hizmeti ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) veya IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|AĞ HİZMETİ|  
        |Hizmet barındırılan IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Denetlenen `<processModel>` Machine.config dosyasında öğe. ASP.NET varsayılan hesaptır.|  
  
    5.  WCF altında icacls.exe gibi bir araç kullanarak çalıştıran hesaba özel anahtarı içeren dosyayı okuma erişimi verin.  
  
         Aşağıdaki kod örneği, ağ hizmeti hesabı okuma izni belirtilen dosya için isteğe bağlı erişim denetimi listesini (DACL) düzenler (: R) dosyasına erişim.  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
- [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
