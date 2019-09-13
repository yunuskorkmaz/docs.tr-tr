---
title: 'Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893307"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma
Aktarım güvenliği kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir. Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz. Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.  
  
 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]çalıştırıyorsanız, Httpcfg. exe aracını kullanın. Bu [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] araçla birlikte yüklenir. İle [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı [Windows XP Service Pack 2 destek araçları](https://go.microsoft.com/fwlink/?LinkId=88606)' na indirebilirsiniz. Daha fazla bilgi için bkz. [Httpcfg Overview](https://go.microsoft.com/fwlink/?LinkId=88605). [Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) , Httpcfg. exe aracının sözdizimini açıklar.  
  
 Çalıştırıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], zaten yüklü olan Netsh. exe aracını kullanın.  
  
 Bu konu, birkaç yordamın nasıl gerçekleştirileceğini açıklamaktadır:  
  
- Bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleme.  
  
- Bir sertifikanın parmak izini alma (aşağıdaki iki yordam için gereklidir).  
  
- Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama.  
  
- Bir bağlantı noktası yapılandırmasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme.  
  
- Bir bağlantı noktası numarasından SSL sertifikası siliniyor.  
  
 Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları olması gerektiğini unutmayın.  
  
### <a name="to-determine-how-ports-are-configured"></a>Bağlantı noktalarının nasıl yapılandırıldığını belirleme  
  
1. Veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ' de, aşağıdaki örnekte gösterildiği gibi, sorgu ve SSL anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için Httpcfg. exe aracını kullanın. [!INCLUDE[wxp](../../../../includes/wxp-md.md)]  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. ' [!INCLUDE[wv](../../../../includes/wv-md.md)]De, aşağıdaki örnekte gösterildiği gibi, geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh. exe aracını kullanın.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Bir sertifikanın parmak izini almak için  
  
1. İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)ile sertifikaları görüntüleyin.  
  
2. Sertifikanın parmak izine erişin. Daha fazla bilgi için [nasıl yapılır: Bir sertifikanın](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)parmak izini alın.  
  
3. Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.  
  
4. Onaltılık karakterler arasındaki tüm boşlukları kaldırın. Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Bir SSL sertifikasını bir bağlantı noktası numarasına bağlamak için  
  
1. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "ayarla" modunda Httpcfg. exe aracını kullanın. Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-I** anahtarı sözdizimine `IP`sahiptir:`port` ve araca sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir. İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.  
  
    - **-H** anahtarı, sertifikanın parmak izini belirtir.  
  
2. İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - **Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.  
  
    - **Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve yalnızca ' i r. exe aracının **-ı** anahtarı gibi işlevleri belirtir.  
  
    - **AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Bir bağlantı noktası numarasına bir SSL sertifikası bağlamak ve istemci sertifikalarını desteklemek için  
  
1. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Veya[!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de, aktarım katmanında X. 509.952 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi, Httpcfg. exe ' ye ek bir komut satırı parametresi geçirin.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** anahtarı, n 'nin `n` 1 ile 7 arasında bir sayı olduğu sözdizimidir. 2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez. 3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir. Diğer değerlerin davranışı için bkz. HttpCfg. exe yardımı.  
  
2. ' [!INCLUDE[wv](../../../../includes/wv-md.md)]De, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Bir bağlantı noktası numarasından bir SSL sertifikası silmek için  
  
1. Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg. exe veya Netsh. exe aracını kullanın. Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] içinde, DELETE ve SSL anahtar sözcükleriyle Httpcfg. exe aracını kullanın. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Parmak izini belirtmek için `IP`:`port` Number ve **-h** anahtarını belirtmek için **-ı** anahtarını kullanın.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir kendi kendine barındırılan hizmetin aktarım güvenliği için ayarlanmış <xref:System.ServiceModel.WSHttpBinding> sınıfını kullanarak nasıl oluşturulacağını gösterir. Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
