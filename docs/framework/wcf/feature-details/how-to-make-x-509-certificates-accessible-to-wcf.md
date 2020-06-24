---
title: 'Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme'
description: X. 509.440 sertifikasını WCF 'ye erişilebilir hale getirme hakkında bilgi edinin. Uygulama kodu, sertifika deposu adını ve konumunu belirtmelidir. Başka gereksinimler olabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 5cc1118640bcf1262d88cb8cdb39939ae315cae3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246876"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme
X. 509.440 sertifikasını Windows Communication Foundation (WCF) erişilebilir hale getirmek için, uygulama kodunun sertifika depolama adını ve konumunu belirtmesi gerekir. Bazı durumlarda, işlem kimliğinin X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya erişimi olmalıdır. Bir sertifika deposundaki bir X. 509.440 sertifikasıyla ilişkili özel anahtarı almak için, WCF 'nin bunu yapması için izni olmalıdır. Varsayılan olarak, yalnızca sahip ve sistem hesabı bir sertifikanın özel anahtarına erişebilir.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>X. 509.440 sertifikalarını WCF 'ye erişilebilir hale getirmek için  
  
1. WCF 'nin, X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya okuma erişiminin çalıştığı hesaba izin verin.  
  
    1. WCF 'nin X. 509.952 sertifikası için özel anahtara okuma erişimi gerektirip gerektirmediğini belirleme.  
  
         Aşağıdaki tabloda, bir X. 509.440 sertifikası kullanılırken özel bir anahtarın kullanılabilir olup olmadığı ayrıntılı olarak verilmiştir.  
  
        |X. 509.440 sertifika kullanımı|Özel anahtar|  
        |---------------------------|-----------------|  
        |Giden bir SOAP iletisini dijital olarak imzalama.|Yes|  
        |Gelen SOAP iletisinin imzası doğrulanıyor.|No|  
        |Giden bir SOAP iletisi şifreleniyor.|No|  
        |Gelen SOAP iletisinin şifresini çözme.|Yes|  
  
    2. Sertifika depolama konumunu ve sertifikanın depolandığı adı saptayın.  
  
         Sertifikanın depolandığı sertifika depolama alanı, uygulama kodunda ya da yapılandırmada belirtilir. Örneğin, aşağıdaki örnek, sertifikanın `CurrentUser` adlı sertifika deposunda bulunduğunu belirtir `My` .  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Sertifika için özel anahtarın, [FindPrivateKey](../samples/findprivatekey.md) aracını kullanarak bilgisayarda bulunduğunu belirleme.  
  
         [FindPrivateKey](../samples/findprivatekey.md) aracı sertifika depolama adı, sertifika depolama konumu ve sertifikayı benzersiz olarak tanımlayan bir şeyi gerektirir. Araç, sertifikanın konu adını ya da parmak izini benzersiz bir tanımlayıcı olarak kabul eder. Bir sertifikanın parmak izini belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir sertifikanın parmak Izini alma](how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Aşağıdaki kod örneği, [FindPrivateKey](../samples/findprivatekey.md) `My` `CurrentUser` bir parmak izine sahip içindeki depodaki bir sertifika için özel anahtar konumunu tespit etmek üzere FindPrivateKey aracını kullanır `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. WCF 'nin altında çalıştığı hesabı belirleme.  
  
         Aşağıdaki tabloda, belirli bir senaryo için WCF 'nin çalıştığı hesabın ayrıntıları verilmiştir.  
  
        |Senaryo|İşlem kimliği|  
        |--------------|----------------------|  
        |İstemci (konsol veya WinForms uygulaması).|Şu anda oturum açmış olan kullanıcı.|  
        |Kendi kendine barındırılan hizmet.|Şu anda oturum açmış olan kullanıcı.|  
        |IIS 6,0 (Windows Server 2003) veya IIS 7,0 (Windows Vista) içinde barındırılan hizmet.|AĞ HIZMETI|  
        |IIS 5. X (Windows XP) içinde barındırılan hizmet.|`<processModel>`Machine.config dosyasındaki öğe tarafından denetlenir. Varsayılan hesap ASPNET ' dir.|  
  
    5. icacls.exe gibi bir araç kullanarak WCF 'nin altında çalıştığı hesaba özel anahtarı içeren dosyaya okuma erişimi verin.  
  
         Aşağıdaki kod örneği, ağ HIZMETI hesabına dosyaya okuma (: R) erişimi vermek için belirtilen dosya için isteğe bağlı erişim denetimi listesini (DACL) düzenler.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FindPrivateKey](../samples/findprivatekey.md)
- [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Sertifikalarla Çalışma](working-with-certificates.md)
